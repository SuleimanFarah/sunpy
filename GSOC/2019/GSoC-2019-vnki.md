# Project Proposal

## Project: Remote data in SunPy

- Name: Vishnunarayan K I
- Organisation: SunPy

#### Personal Info

- Time zone: UTC+05:30
- GitHub handle: [vn-ki](https://github.com/vn-ki)

#### Education

- University: [Indian Institute of Technology, Indore](http://iiti.ac.in/)
- Major: Computer Science
- Current Year: 2nd year

###### Open Source background and Programming experience

- Programming Languages: Python, golang, C++, C, JavaScript/TypeScript, Flutter/Dart, Java(Basic knowledge)
- Contributions to SunPy:
  - GSoC 2018 student with SunPy.
  - I have 24 merged PRs on SunPy repo. [Link](https://github.com/sunpy/sunpy/pulls?q=is%3Apr+sort%3Aupdated-desc+author%3Avn-ki+is%3Aclosed)
- Contributions to other repos:
  - Co-maintainer for [mps-youtube](https://github.com/mps-youtube), [pafy](https://github.com/mps-youtube/pafy) and
    [spotify-downloader](https://github.com/ritiek/spotify-downloader). All python projects.

My personal python projects are:

- [anime-downloader](https://github.com/vn-ki/anime-downloader) (Python)
- [codechef-cli](https://github.com/vn-ki/codechef-cli) (Python)
- [YoutubePlayer](https://github.com/vn-ki/YoutubePlayer) (Python)

I think I have enough experience with python development to produce high quality, testable code.
Therefore I think I am a good fit for this project.

## Design/Implementation

The requirements mentioned in the [issue](https://github.com/sunpy/sunpy/issues/1939) are:
>
> 1. Data is downloaded and cached to `$HOME/sunpy/data/...` when first needed.
> 2. There is some validation that the data has been transferred correctly (sha hashes etc).
> 3. There is a mechanism by which we can allow users to re-download data.
> 4. The download code supports multiple mirrors.

`remote_data_manager` will be a singleton. This makes sense because it is not to be
customized after once initialized.

`remote_data_manager` will handle these in the methods mentioned below:

1. Data download will use a downloader

`remote_data_manager` will be downloader agnostic. parfive is a good candidate for a downloader.
`astropy.utils.data.download_file` is also a perfectly fine candidate.

The downloader according to the design being proposed should be provided using the
constructor injection design pattern. This will mean that the manager is totally downloader agnostic.

2. Validation

This should be some hash which is calculated from the file. SHA-1 is a good candidate because it's fast.

A decorator called `require` is proposed to notify the data manager the requirement of a file by a certain
function.

```python
def require(
  name: str,
  urls: List[str],
  shasum: str,
)
```

This function can have `**kwargs` which can be used to specify arguments specific to the downloader.

The flow of `require` would be:

1. The function checks if the file exists locally and hash matches.
2. If exists, then proceed normally.
3. If the file does not exist, the file will be downloaded from the URL.
4. The hash of the file downloaded is computed and is checked with the provided hash.
    If the hash matches, proceed normally.
    If it does not match, retry from step 3 with the next mirror URL.
    If there are no mirror URLs left, raise an `Exception`.

If the file has been updated on the server and the hash does not match the mentioned hash, an `Exception`
is thrown.

3. Redownload

There will be two functions to re-download the data.

- `skip_hash_check`: As the name mentions, will skip the hash check add download the latest file.
  It can be a context manager. So the usage will look like:

  ```python
  with remote_data_manager.skip_hash_check():
    myfunction()
  ```

- `replace_file(name, url, shasum=None)`: `replace_file` will be a context manager and can be used to
  replace a file to be used by a function with a newer file. `shasum` will be an optional parameter.
  If not provided the latest file on the server will be used.

  This is different from `skip_hash_check` because if a function uses more than one file, user
  can selectively replace files and provide new mirror URLs.

### Cache storage

The cache metadata will be stored using sqlite.
This is inspired by the [implementation](https://github.com/reclosedev/requests-cache/tree/master/requests_cache/backends)
of `requests-cache`. `requests-cache` support a number of backends for cache storage (SQLite,
Redis, MongoDB, dynamodb etc.). Even though remote data manager does not need multiple backends,
following a similar design to that will give us more extensibility in the future and an easier to
mock backend for testing purposes.

The content of the metadata will be:

- hash: hash of the file. (primary key)
- filepath: Path to the file. (Ideally not the absolute path, so that the sunpy data dir can
    be changed without conflicts)
- last_modified: Modified datetime on the server (Not the downloaded file). This can be useful when
  using the function `skip_hash_check`. The file can be checked using the modified date of the
    file on the server with the `last_modified` of the hashed file.
    This can be easily achieved by getting `Last-Modified` from response headers and it is possible to get this without downloading the entire file.
- functions: The names of the functions using the file.

The file can be stored under a directory which is named depending on the function (maybe function name).

One thing to investigate here is whether it is possible to do the cache metadata without sqlite at all.
If we are ok with redownloading files if multiple functions use the same file, then it is possible to
not use sqlite and use a JSON file per function instead.

## Additional tasks

[`parfive`](https://github.com/cadair/parfive) is an async parallel downloader built for sunpy.
This is primarily used for downloading sample data for SunPy. parfive is a good candidate
downloader for remote data manager. Currently, parfive is only performant when downloading files in parallel.

The additional task is to implement downloading by parts for parfive so that the downloads
can be accelerated when downloading a single file. Downloading by parts and recombining them afterward is how most download accelerators work.

I already have the experience of doing this for a personal project.

# Project Plan

### Community Bonding Period (May 7 - May 26)

My vacations start on May 3rd. So I would like to code at least a small part during this period.

I am familiar with most libraries that are going to be used and have a good idea about the python
features that will be used like context managers and decorators. I also have experience with pytest
and general testing procedures like mocking past GSoC and from personal projects.

The first task here would be to finalize on the API design.
One of the important things here is deciding on the method of storing cache.
The next task is to start coding the skeleton of the remote data manager.

I like to write tests with the code I write so some tests will be done with tasks itself.
___

### Coding Period Begins

___

### Week 1 (May 27 - June 2)

- Implement the caching mechanism.

### Week 2 - Week 3 (June 3 - June 16)

- Implement the functions of remote data manager mentioned above.

### Week 4 - Week 5 (June 17 - June 23)

- Integrate the data manager with the cache.

___

### Phase 1 Evaluation

___

### Week 6-7 (June 25 - July 7)

- API review. Investigate additions to the API and feasibility of the design.

### Week 8 (July 8 - July 14)

- Document and test the tasks until now.

### Week 9 (July 15 - July 21)

- Implement parfive download by parts complete with tests and documentation.

___

### Phase 2 Evaluation

___

### Week 10 - Week 11 (July 23 - August 6)

- Finish up any remaining testing and documentation.
- Example for the gallery.

### Week 12 - Week 13 (August 7 - August 25)

- Complete written documentation
- Add necessary developer documentation
- Work on possible improvements to parfive

___

### Final Evaluation

___

## GSoC

### Have you participated previously in GSoC? When? Under which project?

**Yes**, I participated in 2018 under SunPy.

### Are you also applying to other projects?

**Yes**, I am also applying for Prometheus under CNCF.

### Commitments

I don't have any other internship or work during this summer. I have no plans for any vacations either.

### Eligibility

Yes, I am eligible to receive payments from Google.

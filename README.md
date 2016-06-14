# hexo-deployer-s3-cloudfront

Amazon S3 and Cloudfront deployer plugin for [Hexo](http://hexo.io/). Based on Josh Strange's orginial plugin.

## Installation

``` bash
$ npm install hexo-deployer-s3-cloudfront --save
```

## Usage

Add the plugin in the plugins list in `_config.yml`:

```plugins:
- hexo-deployer-s3-cloudfront
```

and configure the plugin in the same file with:

``` yaml
# You can use this:
deploy:
  type: s3-cloudfront
  bucket: <S3 bucket>
  aws_key: <AWS id key>  // Optional, if the environment variable `AWS_KEY` is set
  aws_secret: <AWS secret key>  // Optional, if the environment variable `AWS_SECRET` is set
  concurrency: <number of connections> // Optional
  force_overwrite: <true/false> // Optional: If existing files should be forcefully overwritten on S3. Default: true
  region: <region>  // Optional, default: us-standard
  cf_distribution: <cloudfront distribution> // Which distribution should be invalidated?
  headers: <headers in JSON format> // pass any headers to S3, usefull for metadata cache setting of Hexo assets
```
#### Example: header Cache-Control

``` yaml
deploy:
  type: s3-cloudfront
  bucket: my-site-bucket
  cf_distribution: mydistributionid
  headers: {CacheControl: 'max-age=604800, public'}
```

This will set "Cache-Control" header in every file deployed to max-age 1 week. This solves "Leverage browser caching" on most page speed analyzers. For custom metadata use:

``` yaml
  headers: {Metadata : { x-amz-meta-mykey: "my value" }}
```

## Contributors

- Wouter van Lent ([wouter33](https://github.com/wouter33))
- Josh Strange ([joshstrange](https://github.com/joshstrange); original implementation)
- Josenivaldo Benito Jr. ([JrBenito](https://github.com/jrbenito))

## License

MIT

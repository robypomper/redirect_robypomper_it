# Redirect robypomper.it

SYSTEM repository for robypomper.it redirects.

This repo contains only a simple `index.html` file that will be published as
[GitHub Pages](https://pages.github.com/). At the same time the DNS records for
the `robypomper.it` use the GitHub.io servers as `A` records.

So, when the user require the [http[s]://[www.]robypomper.com](https://www.robypomper.it)
url the DNS redirects it to the GitHub.io server where the `index.html` (or the
`404.html`) page is returned.<br/>
If the user required an `http` url, the GitHub.io server redirects it to the
`https` version of the same url.<br/>
Then, this page contains a JavaScript code that replace the `window.location`'s
protocol and domain.

That's all.


## Run

Open a browser and go to the one of the following links:
* [http://robypomper.it](http://robypomper.it)
* [https://robypomper.it](https://robypomper.it) (WARNING on certificate's name)
* [http://www.robypomper.it](http://www.robypomper.it)
* [https://www.robypomper.it](https://www.robypomper.it)

After some redirect it should display the [https://www.robypomper.org](https://www.robypomper.org)
page and url.


## Test

Execute the following `curl` command into a shell:

```shell
curl -v -L -o /dev/null http://robypomper.it 2>&1 | egrep -i "> Host:|> GET|* Connected|< Server|< Location|SSL:"

* Connected to robypomper.it (185.199.111.153) port 80 (#0)
> GET / HTTP/1.1
> Host: robypomper.it
< Server: GitHub.com
< Location: https://www.robypomper.it/

* Connected to www.robypomper.it (185.199.109.153) port 443 (#1)
> GET / HTTP/2
> Host: www.robypomper.it
< server: GitHub.com
```


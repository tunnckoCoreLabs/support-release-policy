# Support & Release Policy
Supported Node.js release lines and plan how we proceed in future, how and when we drop support for certain Node.js release lines.

We only support latest 2 _even-numbered_ Node.js release lines, until they goes into Maintenance mode _or_ until the Node.js cut new even-numbered Current release. When that happen we drop support for the release line that gone on maintenance mode, which means two things: 

1. bump major release of a package, and
2. replace that Node.js version in CI testing with the new Current release version. 

Though, it may still be possible certain package to work on newer or older Node.js versions.

How we do that? We forcing it by using [package.json `engines.node`](https://docs.npmjs.com/files/package.json#engines) property in each package. So, if you want to install certain package on different than supported Node.js versions, then you should use the `--ignore-engines` flag in your package manager. This makes things pretty visible and explicit for both sides.

![Node.js LTS Release Schedule](https://images.ctfassets.net/hspc7zpa5cvq/7o3kha5RgAGCImaw84yiEY/19957b9f448b1431e9664ed94e996d74/nodejs-lts-release-schedule_preview.png)


Consider the following example and above graph, which starts from October 2018. 

Lets say we are in May 2019. We have Node.js v10 Active LTS release since October 2018, and we have v12 Current release since April 2019. We will support both versions, until April 2020.

Through that month (april 2020) there will happen three important events: 

1. Node.js team will move the Current (v12) into Active LTS mode (v12-LTS)
2. Node.js team will release new even-numbered release which will become the new Current (v14-Current)
3. Once both of above happen, we drop support for the v10-LTS release as described previously

So it's recommended by both us and the community to migrate to at least the lastest Active LTS Node.js release, which by that time will be v12. 

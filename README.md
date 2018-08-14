# Support & Release Policy
Supported Node.js release lines and how we integrate seamlessly with the Node.js's Release Cycle.

## Node.js's Versioning Terminology
For more info read [Understanding How Node.js Release Lines Work](https://nodesource.com/blog/understanding-how-node-js-release-lines-work/) and the Node.js's https://github.com/nodejs/Release page.

### General Versioning Terminology
- **Release Line:** A release line is defined as any major version of Node.js. For example, Node.js 6, Node.js 7, Node.js 8, Node.js 9, and so on are all release lines.
- **SemVer:** SemVer stands for Semantic Versioning, and is the versioning mechanism that both the Node.js releases and the majority of the Node.js ecosystem use for versioning.
**Major Release:** Major Releases are for incompatible API changes, from version to version. Major releases can also include changes that would normally be included as Minor or Patch releases.
- **Minor Release:** Minor Releases include backward compatible functionality changes. Minor releases can also include changes that would normally be included as Patch releases.
- **Patch Release:** Patch releases include non-breaking bug fixes and security patches.

### Release Terminology
- **Current:** Current is a term used to refer to the most recent Node.js release line (yes, that's singular) that will be supported and open to non-trivial changes until the next major release.
- **LTS:** LTS is an acronym for Long-Term Support, and is applied to release lines (yes, that's plural) that will be supported and maintained by the Node.js project for an extended period of time.
  + **Active:** An Active LTS release line is one that is being actively maintained and upgraded, including backporting newer non-breaking features, functionality, and improvements, addressing bugs, and patching security vulnerabilities.
  + **Maintenance:** A Maintenance LTS release line is a Node.js LTS release line that's nearing End of Life (EOL) and will only receive bug fixes and security patches for a short window of time.
- **EOL:** EOL is an acronym for End of Life. Node.js versions that are EOL are no longer maintained, and will not be patched with fixes for bugs or known security vulnerabilities.
Cutting/Shipping: Cutting and shipping are both terms used to refer to the actual release of any given version (major, minor, or patch) of Node.js. These terms aren't specific to Node.js but are used relatively often by the Node.js contributor base.

## Our Support

We only support latest 2 _even-numbered_ Node.js release lines, until they goes into Maintenance mode _or_ until the Node.js team cut new even-numbered Current release. When that happen we drop support for the release line that gone on maintenance mode, which means 3 things: 

1. we bump major release of a certain package,
2. remove that Node.js release line from CI testing, and
2. add the new Current release line for CI testing.

Though, it may still be possible certain package to work on newer or older Node.js versions.

How we do that? We forcing it by using [package.json `engines.node`](https://docs.npmjs.com/files/package.json#engines) property in each package. So, if you want to install certain package on different than supported Node.js versions, then you should use the `--ignore-engines` flag in your package manager. This makes things pretty visible and explicit for both sides.

![Node.js LTS Release Schedule](https://images.ctfassets.net/hspc7zpa5cvq/7o3kha5RgAGCImaw84yiEY/19957b9f448b1431e9664ed94e996d74/nodejs-lts-release-schedule_preview.png)


Consider the following example and above graph, which lets say starts from October 2018. 

Lets say we are in May 2019. We have Node.js v10 Active LTS release since October 2018, and we have v12 Current release since April 2019. We will support both versions, until April 2020.

Through that month (april 2020) there will happen three important events: 

1. Node.js team will move the Current (v12) into Active LTS mode (v12-LTS)
2. Node.js team will ship new even-numbered release which will become the new Current (v14-Current)
3. Once both of above happen, we drop support for the v10-LTS release as described previously

So it's recommended by both us and the community to migrate to at least the lastest Active LTS Node.js release, which by that time will be v12. 

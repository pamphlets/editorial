# Editorial

Write together as peers

## Install

```
$ npm install editorial
```

## Use

The following example creates a working collaborative editor.

```js
var Editorial = require('editorial')

var url = new URL(window.location)
var name = url.searchParams.get('username') || 'Incognito'
var room = url.searchParams.get('room')
var editorial = new Editorial(document.body, room, { name })

if (!url.searchParams.has('room')) {
  url.searchParams.set('room', editorial.room)
  history.pushState({}, '', url)
}
```

Using Editorial you can collaboratively edit texts without relying on a central server. Each user has a copy of the collaborative document on their own device stored inside [IndexedDB](https://en.wikipedia.org/wiki/Indexed_Database_API). Editorial then uses [WebRTC](https://en.wikipedia.org/wiki/WebRTC) to make a direct connection between the browsers of different users to exchange changes to the document. Conflicts are resolved by the algorithms that underly [Yjs](https://yjs.dev)'s shared data types. This means that we don't need any central authority to facilitate collaboration. Not for storage, not for data exchange, and not for conflict resolution.

The editor is built on [Pamphlet](https://github.com/pamphlets/pamphlet), which provides a focused editing experience on top of Markdown. If you don't need any collaborative features, it's best to use Pamphlet directly.

## Credit

Most of the heavy lifting by [ProseMirror](https//prosemirror.net) for the editing and [Yjs](https://yjs.dev) for collaboration and communication.

## License

Apache-2.0

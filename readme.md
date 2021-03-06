<p align="center">
  <img src="https://raw.githubusercontent.com/siddharthkp/keep/master/art/logo.png" height="200px"/>
  <br><br>
  <b>keep lets you store data for your apps with zero setup</b>
  <br>
</p>

&nbsp;

### sponsor

<a target='_blank' rel='nofollow' href='http://app.codesponsor.io/link/LhLT2c31ydJzdLUuSR9f8mCA/siddharthkp/keep'>
  <img alt='Sponsor' width='888' height='68' src='http://app.codesponsor.io/embed/LhLT2c31ydJzdLUuSR9f8mCA/siddharthkp/keep.svg' />
</a>


&nbsp;

### the problem

&nbsp;

I see myself repeating the same steps with every side project:

1. create a data store
2. add authentication layer on top of the store
3. write CRUDs on top of the store
4. (optional) create an extra layer to protect secrets/config if the app will live on other folks' machine (example: npm packages/cli tools)

&nbsp;

### what i want

1) Zero config setup

```
keep new
```

spit out secrets in a .env file

good to have: copy the secrets into a custom config file

&nbsp;

2) Super simple API

```js
  import keep from 'keep'
  // auto initialise

  keep.add('users', {name: 'Siddharth', handle: 'siddharthkp'})
  // returns a promise, resolves to give id/hash

  keep.get('users', {id: 1})
  // {name: 'Siddharth', handle: 'siddharthkp'}

  keep.get('repos', {user_id: 1})
  // [{name: 'bundlesize', forks: 68}, {name: 'db', forks: 0}]

  keep.find('users', {name: 'sid'})
  // [{id: 1, name: 'Siddharth', handle: 'siddharthkp'}, {id: 9, name: 'Sid Vicious', handle: 'vicious'}]

  keep.delete('users', {id: 1})
```

good to have:

```js
  // support for custom config
  import { init } from 'keep'
  init({identifier: 'my_app', secret: 'super_secret'})

  // prefetch all entries in a table and store in cache for perf
  keep.prefetch('users')

  // prefetch data from all tables for a user and store in cache for convenience
  keep.prefetch({user_id: 1})
```

&nbsp;

### sounds exciting?

give it a star, that's a proxy for demand :smile:

or help out with the implementation, DM me on [twitter](https://twitter.com/siddharthkp)

&nbsp;

### inspiration/prior art

- inspired by the simplicity of [zeit/now](https://zeit.co/now)
- [firebase by google](https://firebase.google.com)
- [pronto by Vadim Demedes](https://github.com/vadimdemedes/pronto)

&nbsp;

# mferbase

> The entire mfers NFT universe in a single git repository.

mferbase is the entire mfers NFT Universe stored in a single Git repository. It's made up of:

1. **DB:** The entire metadata database stored in a single [SQLite DB file](mixtape.db)
2. **FILES:** All IPFS files stored under [ipfs](ipfs) folder without having to run your own IPFS node!

All of the above stored and downloadable with a single `git clone`.

- Try the Demo: https://mixtape-network.gitlab.io/mferbase
- Stay updated or ask questions on Twitter: https://twitter.com/skogard
- Ask questions in Discord: https://discord.gg/BZtp5F6QQM

---

# Why?

When you work with NFTs you often need to query some 3rd party API.

But if you think about it, you really don't need to rely on them for working with NFT assets (images, videos, files, etc.) and metadata (name, description, attributes, etc.). After all, they're all immutable!

With mferbase, you can simply download the entire NFT universe through a single git clone and work with it 100% locally and offline. Use it in your app as often as you want, for free, forever!.

1. No IPFS connection required
2. No Blockchain connection required
3. No 3rd party API required

---

# How it works

1. **DB:** The entire database is stored as a single immutable SQLite file at [mixtape.db](mixtape.db). This file was constructed by crawling the Ethereum blockchain once (You only need to do it once, since NFT metadata are immutable!)
2. **FILES:** All IPFS files are stored under the IPFS CID name WITHOUT having to run an IPFS node. It's all in this Git repository under [ipfs](ipfs) folder.

## 1. DB

mferbase indexes all properties of the NFT metadata inside a table named **metadata**, inside the [mixtape.db](mixtape.db) DB, and makes them queryable. Here are the attributes indexed:

1. **name:** The `name` attribute of the NFT metadata standard
2. **description:**: The `description` attribute of the NFT metadata standard
3. **image:** The `image` attribute of the NFT metadata standard
4. **attributes:** The `trait_type`/`value` pair inside the `attributes` array. Learn more about the `attributes` array [here](https://docs.opensea.io/docs/metadata-standards#attributes)
5. **other custom attributes:** Other custom metadata may be indexed (if they exist)

Best of all, all this is 100% verifiable and immutable, so you can feel free to use this without worrying about authenticity!


## 2. FILES

mferbase also lets you access all the associated IPFS files WITHOUT running an IPFS node!

Simply clone this git repository and it contains all the IPFS files for the mferbase NFT Universe! You can check out all the files under [ipfs](ipfs).

## 3. WEB APP

mferbase comes with a built-in query engine web app at [index.html](index.html)

Everything is loaded directly from the Gitlab pages built from this repository, serverlessly ([even the DB](mixtape.db) thanks to [sql.js](https://sql.js.org/documentation/)!) 

You can try the web app at https://mixtape-network.gitlab.io/mferbase

---

# Quickstart

## 1. Download

First, clone this repository by running:

```
git clone https://gitlab.com/mixtape-network/mferbase.git
```

## 2. Try the query web app

You can now run the entire mferbase query engine web app on your local machine. **No network connection required since everything is on your machine**.

Simply go into the `mferbase` folder you just downloaded, and run:

```
npx http-server
```

It will start a server at http://localhost:8080 and when you visit, you will be greeted with the query engine web interface.

## 3. Advanced

1. **Playing with the files:** Go into the mferbase folder you just cloned, and play with all the files under the `ipfs` folder.
2. **Playing with the DB:** Remember, the entire DB is just a single SQLite file and you can open it on any SQLite client. Open the `mixtape.db` in [any SQLite client](https://medevel.com/13-sqlite-database-clients-managers/) to directly query the DB with SQL.

---

# Usage

Everything in this git repository is also served over a static website. This repository is made up of largely 3 components, all of which are also published over Gitlab pages:

1. **Metadata DB:** Stored in a single SQLite3 db file: [mixtape.db](mixtape.db)
2. **NFT Files:** Stored under the [ipfs](ipfs) folder
3. **Static Site:** The [index.html](index.html) file is used to render all the NFT files and metadata, providing an instant query interface WITHOUT needing a server

## DB

The DB is stored at [mixtape.db](mixtape.db). Since it's just an SQLite DB file, you can browse and analyze it with [any SQLite clients](https://medevel.com/13-sqlite-database-clients-managers/).


## Files

All the IPFS image files are stored under the [ipfs](ipfs) folder, **with their original IPFS CID preserved.**

## Web

The built-in website lets you quickly query the DB at https://mixtape-network.gitlab.io/mferbase WITHOUT a server. Everything is loaded from the static page, **including the [mixtape.db](mixtape.db) DB.**

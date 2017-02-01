class: center, middle

# try ES2015

---

# Agenda

1. Introduction
1. Description
1. Requirement
1. Installation
1. Usage

---

# Introduction

Babelを用いたES2015のトランスパイル環境です。  
ES2015を試すために作りました。

---

## Description

- ツールは`babel-cli`を使用しています。
- プリセットは`babel-preset-es2015`を使用しています。

---

## Requirement

`node`/`npm`を使います。

---

## Installation

`npm install`を実行します。

---

## Usage

1. `src`ディレクトリ以下にES2015で書かれたjsファイルを配置します。
1. `npm run build`を実行します。
1. `lib`ディレクトリ以下にトランスパイルされたjsファイルが生成されます。

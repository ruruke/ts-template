# NodeJS Application (EN)

## Overview

This project is a Node.js application written in TypeScript. It is built using ESBuild and features logging with Pino.
Prerequisites

    Node.js (22.x or higher recommended)
    pnpm 10.10.0 or higher

Installation

To install dependencies, run the following command:
Shell

pnpm install

Usage
Development Mode

To run the application in development mode:
Shell

pnpm dev

This command builds the application in development mode and runs it immediately.
Build

To build the application, use the following commands:
Development Build
Shell

pnpm build:dev

Production Build
Shell

pnpm build:prod

In the production build, the code is obfuscated using JavaScript Obfuscator.
Run

To run the built application:
Shell

pnpm start

Key Features

    TypeScript: A statically typed superset of JavaScript.
    ESBuild: An extremely fast JavaScript/TypeScript bundler.
    Pino: A high-performance Node.js logging library.
    JavaScript Obfuscator: Code protection for production environments.

GitHub Workflow

This project includes a GitHub Actions workflow for Continuous Integration/Continuous Delivery (CI/CD).
Workflow Configuration
YAML

name: Node.js CI

on:
push:
branches: [ main, master ]
pull_request:
branches: [ main, master ]

jobs:
build:
runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [18.x]

    steps:
    - uses: actions/checkout@v3
    
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'pnpm'
        
    - name: Install pnpm
      uses: pnpm/action-setup@v2
      with:
        version: 10.10.0
        
    - name: Install dependencies
      run: pnpm install
      
    - name: Build (Production)
      run: pnpm build:prod
      
    - name: Test
      run: pnpm test

This workflow performs the following actions:

    Runs on pushes to the main or master branches, or on pull requests to these branches.
    Tests with Node.js 18.x.
    Uses the pnpm package manager.
    Installs dependencies, performs a production build, and runs tests.

Note: The current package.json does not include a test script. Please add a test script to package.json as needed, or remove the test step from the CI configuration.
License

GPL-3.0 license

# NodeJS Application (JA)

## 概要

このプロジェクトは、TypeScriptで書かれたNode.jsアプリケーションです。ESBuildを使用してビルドされ、Pinoによるロギング機能を備えています。

## 前提条件

- Node.js (22.x以上推奨)
- pnpm 10.10.0以上

## インストール

依存関係をインストールするには、以下のコマンドを実行してください：

```shell script
pnpm install
```


## 使用方法

### 開発モード

開発モードでアプリケーションを実行するには：

```shell script
pnpm dev
```


このコマンドは、アプリケーションを開発モードでビルドし、すぐに実行します。

### ビルド

アプリケーションをビルドするには、以下のコマンドを使用します：

#### 開発ビルド

```shell script
pnpm build:dev
```


#### 本番ビルド

```shell script
pnpm build:prod
```


本番ビルドでは、JavaScript Obfuscatorを使用してコードが難読化されます。

### 実行

ビルドしたアプリケーションを実行するには：

```shell script
pnpm start
```


## 主な機能

- **TypeScript**: 型安全なJavaScriptスーパーセット
- **ESBuild**: 高速なJavaScript/TypeScriptバンドラー
- **Pino**: 高性能なNode.jsログライブラリ
- **JavaScript Obfuscator**: 本番環境用のコード保護

## GitHub Workflow

このプロジェクトには、継続的インテグレーション/継続的デリバリー（CI/CD）のためのGitHub Actionsワークフローが含まれています。

### ワークフロー設定

```yaml
name: Node.js CI

on:
  push:
    branches: [ main, master ]
  pull_request:
    branches: [ main, master ]

jobs:
  build:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [18.x]

    steps:
    - uses: actions/checkout@v3
    
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'pnpm'
        
    - name: Install pnpm
      uses: pnpm/action-setup@v2
      with:
        version: 10.10.0
        
    - name: Install dependencies
      run: pnpm install
      
    - name: Build (Production)
      run: pnpm build:prod
      
    - name: Test
      run: pnpm test
```


このワークフローは以下の処理を行います：
- mainまたはmasterブランチへのプッシュ、またはこれらのブランチへのプルリクエスト時に実行
- Node.js 18.x環境でテスト
- pnpmパッケージマネージャーを使用
- 依存関係のインストール、本番ビルド、テストを実行

**注意**: 現在のpackage.jsonにはテストスクリプトが含まれていないため、必要に応じてpackage.jsonにテストスクリプトを追加するか、CI設定からテストステップを削除してください。

## ライセンス

GPL-3.0 license

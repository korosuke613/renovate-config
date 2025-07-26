# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 重要
日本語でのコミュニケーションを優先してください。英語での回答は必要ありません。

## プロジェクト概要

このリポジトリは@korosuke613のRenovate共有可能設定プリセットです。他のリポジトリで拡張できる標準化されたRenovate設定を提供します。

## リポジトリ構造

- `default.json` - メインプリセットを拡張する基本的なRenovate設定
- `renovate.json5` - ベストプラクティス、セキュリティ設定、パッケージルールを含むメイン共有プリセット
- `npm-automerge-deps-minor-patch.json5` - npmのminor/patch依存関係更新を自動マージするプリセット
- `renovate.json5` (modified) - このリポジトリ自身のRenovate設定

## 主要設定詳細

メインプリセット（`renovate.json5`）の内容：
- Asia/Tokyoタイムゾーンでの月次スケジュール
- 安定性のための14日間の最小リリース期間
- 自動マージなしのセキュリティ脆弱性アラート
- サードパーティアクションのGitHub Actions digest固定（actions/*、korosuke613/*、cybozu/*を除く）
- 設定マイグレーション有効

## 使用方法

他のリポジトリは`renovate.json5`に以下を追加してこれらのプリセットを拡張できます：
```json5
{
  $schema: "https://docs.renovatebot.com/renovate-schema.json",
  extends: ["github>korosuke613/renovate-config"],
}
```

npmのminor/patch更新の自動マージには：
```json5
{
  extends: ["github>korosuke613/renovate-config:npm-automerge-deps-minor-patch.json5"],
}
```

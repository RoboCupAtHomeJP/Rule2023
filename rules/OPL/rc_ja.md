# Receptionist

[**日本語**](./rc_ja.md) | [English](./rc_en.md)

参考動画：https://youtu.be/p9ki89buY68 <br>
> **Note**
> この動画は参考動画である．RoboCupのルールによってタスク内容が異なる可能性がある．
> 質問や議論は，GitHubの[Issues](https://github.com/RoboCupAtHomeJP/Rule2023/issues)にて行う．


> **Note**
> このルールはRoboCup2022のReceptionistを参考にRoboCup JapanOpen 2023向けに作成されたものである．スコアシートはRoboCup JapanOpen 2022に基づいている．

## メインゴール (Main Goal)

このタスクでは，ロボットが会場に到着したゲストへの受付を行い，リビングルームに案内する．ロボットはゲストの名前や好きな飲み物等を聞き，ホストに紹介する．また，到着したばかりのゲストに空いている席を案内する．

## フォーカス

システムインテグレーション，ヒューマンロボットインタラクション，人物検出，人物認識

## セットアップ

- **開始地点**: ロボットは，アリーナ内のあらかじめ決められた場所からスタートする．
- **ホスト**: ホストの名前はジョンである．
- **ゲスト**: 二人のゲストにはそれぞれ名前と好みの飲み物が設定されている．到着したゲストはロボットの前にやってくる．ゲストはロボットに部屋の中へ案内され紹介される．二人のゲストはそれぞれ別々にやってくる．

> **Note**
> 名前リストや開始地点等の情報はセットアップデイまでに以下のリポジトリで公開される．
> https://github.com/RoboCupAtHomeJP/AtHome2023/opl

## シナリオ

1. スタートフェーズ
   1. **競技時間**: 競技時間は**7分間**である．
   2. **配置**: レフェリーは，チームに対しロボットをスタート位置へ移動させるよう指示する．
   3. **スタート**: レフェリーはスタートの合図を出し，タイマーをスタートさせる．チームは最後の簡単なセットアップ（スタートボタンを押す等）を完了し，エリアを離れる．ボタンを2つ以上押すなど複雑なセットアップ手順の実施は認められない．
2. レセプションフェーズ
   1. **ゲストの検出**: ロボットは会場に到着し，部屋に入ってきたゲストを検出する．
   2. **ゲストの受付**: ロボットはゲストの名前と好きな飲み物についての情報を聞く．ロボットが名前や好きな飲み物について理解できなかった場合，もう一度発言を繰り返すように要求することができる．
   3. **ゲストの紹介**: 到着したゲストをホストへ紹介する．ロボットは紹介する人を指さし，名前と好きな飲み物について紹介する．
3. ガイドフェーズ
   1. **案内**: ゲストを空いている席へ案内し，座らせる．ロボットはゲストが座れる場所（空席）を指差す．
   2. **席の入れ替え**: 新しいゲストが来ると，リビングにいるゲストたちの場所を交換する場合がある．
4. ボーナスフェーズ
   1. ロボットは1人目のゲストについて，4つの特徴（例）服の色，髪の色，性別，年齢）を2人目のゲストに対して述べるとボーナス点を獲得できる．

ロボットが人間とやりとりする際，その対象となる相手を注意を向ける必要がある．例えばロボットは，一人を指差しもう一人の方向を向いて話す，二人を交互に見ながら話す．

## デウスエクスマキナ

本タスクでは，次のデウスエクスマキナが採用される．デウスエクスマキナを使用した場合，該当アクションの点数は入らないが，より簡単な手法でアクションをスキップし，タスクを継続することができる．

| Action             | Bypassing                                                            |
| ------------------ | -------------------------------------------------------------------- |
| 人間の特定         | 人間にマーカを持たせることで，人間を特定する         ．              |
| 空いている席の特定 | 空いている席にマーカを設置することで，席が空いていることを特定する． |

## スコアシート

| Action | Score |
| ------ | ----- |
| **メインタスク** |   |
| 1人目のゲストをホストに紹介する             |  |
| &emsp; 1人目のゲストの名前を紹介する        | $25$ |
| &emsp; 1人目のゲストの好きな飲み物を紹介する | $25$ |
| &emsp; 紹介中，1人目のゲストに注意を向ける   | $35$ |
| 1人目のゲストに空いている席を案内する         |  |
| &emsp; 空席を検出する                     | $60$ |
| &emsp; 空席を指差す／向いて提供する         | $65$ |
| 2人目のゲストをホストに紹介する              |  |
| &emsp; 2人目のゲストの名前を紹介する        | $25$ |
| &emsp; 2人目のゲストの好きな飲み物を紹介する | $25$ |
| &emsp; 紹介中，2人目のゲストに注意を向ける   | $35$ |
| 2人目のゲストに空いている席を案内する         |  |
| &emsp; 空席を検出する                     | $60$ |
| &emsp; 空席を指差す／向いて提供する          | $65$ |
| **ボーナスタスク**                         |   |
| &emsp; 1人目のゲストについて4つの特徴を説明する        | $4 \times 20$ |
| **デウス・エクス・マキナ** |  |
| &emsp; マーカーを用いて人間を特定し注意を向ける | $-17.5$ |
| **ペナルティ**                            |   |
| &emsp; リスタート | $直後に獲得した点数 \times -0.5$|
| &emsp; 不参加（無断）                      | $-500$  |
| **合計**                                  | $500$ |

## TCによる指示

- 準備
  - ボランティア3名に名前と飲み物を割り当てる．
  - リビングルームに人を配置する（配置し直す）．
- アナウンス（セットアップデイ）
  - タスクの開始地点，ホストの場所を公開する．
  - 人物，飲み物の名称リストを公開する．

## レフェリーの動き

レフェリーは各チームから数名選出され，他チームの競技において以下を行う．

- 競技開始30分前に集まり，説明を受け，スコアシートを受け取る．
- シナリオに記載のレフェリーとして行動する．
- 競技を採点する．
- 他のTCと採点内容を確認する．
- スコアシートを提出する．

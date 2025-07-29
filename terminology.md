# IPv6対応UPnP 関連用語定義

ゲーム・エンタメのネットワーク接続性に関する課題検討WG IPv6対応UPnP実装・検証SWG

Copyright (c) 2025 JAIPA

## 変更履歴

- rev.20250729a（2025年7月29日）
  - 初版

## 目次

1. 本ドキュメントについて
2. SWGにて使用される用語と概念

## 1. 本ドキュメントについて

本ドキュメントは、国内におけるIPv6対応UPnPの活用促進を目的として作成・更新されています。

IPv6対応UPnPを取り巻く用語は標準化が十分ではないため、適切な議論・説明を行うためには、事前の定義が必要不可欠です。

そのため、このRepository内のドキュメントを含む、本SWGから情報発信で扱う未標準用語は、このドキュメントで定義するものとする。

> OCF（Open Connectivity Foundation） ではIDGv2のフルスペック実装をもってIPv6対応としている。
>
> 一方で、本SWGでは実運用に即した定義を別途行っている。

## 2. SWGにて使用される用語と概念

### IPv6対応UPnP

WANIPv6FirewallControl:1 Service に対応し、IPv6 MulticastによるDiscovery 及び AddPinhole Action による Firewall 制御 を行えるUPnP実装を、IPv6対応UPnPと定義する。

### Pinhole機能

WANIPv6FirewallControl:1 Service に対応し、AddPinhole ActionによるFirewall制御を行うことが出来るルータ側の機能をPinhole機能と定義する。

### 多段ND Proxy

IPv6通信に対するSPI（Stateful Packet Inspection）ないし、同等のフィルタリング処理を行うルータが、多段構成で複数存在する状態を、多段ND Proxy（Neighbor Discovery Proxies）と定義する。

この環境においては、クライアントがIPv6対応UPnPを活用しても、フィルタリング挙動（RFC4787）が Endpoint Independent Filtering とならないことが多い。

> 概念としては、IPv4でいうところの多段NAT構成のIPv6版ともいえる

### IPv6対応ポート解放

IPv6対応UPnP機能を活用、もしくは、ルータの管理画面からFirewall設定等を行うことで以下の要件を満たす環境へと、クライアントのIPv6通信環境を変化させること。

- クライアントから見た通信先に対するフィルタリング挙動（RFC4787）が Endpoint Independent Filtering を満たす
  - NAT66環境/NPTv6環境等においては、マッピング挙動（RFC4787）が Endpoint Independent Mapping も合わせて満たす
- エンドポイント間の通信に対するSPI （Stateful Packet Inspection）のセッションが生成されたのと同等の状態をルータが内部的に持つ（= インターネット側から開始された通信を、LAN側のクライアントが受信可能な状態）

> IPv4におけるポート解放と明示的に区別するために、このように定義する

### ポート解放

UPnP機能を活用、もしくは、ルータの管理画面からNAPT・Firewall設定等を行うことで以下の要件を満たす環境へと、クライアントのIPv4通信環境を変化させること。

- クライアントから見た通信先に対するフィルタリング挙動（RFC4787）が Endpoint Independent Filtering を満たす
- クライアントから見た通信先に対するマッピング挙動（RFC4787）が Endpoint Independent Mapping を満たす
- エンドポイント間の通信に対するAddress binding（RFC2663）が生成されたのと同等の状態をルータが内部的に持つ

> 本来IPv4対応ポート解放と明示的に呼びたいが、標準化はされていないものの既に普及している表現であるため、単にポート解放と呼ぶ


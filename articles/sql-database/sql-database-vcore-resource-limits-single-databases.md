---
title: Azure SQL Database の仮想コアベースのリソース制限 - 単一データベース | Microsoft Docs
description: このページでは、Azure SQL Database の単一データベースに対するいくつかの一般的な仮想コアベースのリソース制限について説明します。
services: sql-database
author: CarlRabeler
manager: craigg
ms.service: sql-database
ms.custom: DBs & servers
ms.topic: conceptual
ms.date: 08/01/2018
ms.author: carlrab
ms.openlocfilehash: 603a6e2f3ce744d792ad9c9be20622c65a37dda3
ms.sourcegitcommit: 96f498de91984321614f09d796ca88887c4bd2fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39414608"
---
# <a name="azure-sql-database-vcore-based-purchasing-model-limits-for-a-single-database"></a>Azure SQL Database の単一データベースに対する仮想コアベースの購入モデルの制限

この記事では、仮想コアベースの購入モデルを使用した、Azure SQL Database の単一データベースに対する詳細なリソース制限について説明します。

DTU ベースの購入モデルの制限については、[SQL Database の DTU ベースのリソース制限](sql-database-dtu-resource-limits.md)に関する記事をご覧ください。

> [!IMPORTANT]
> 場合によっては、未使用領域を再利用できるようにデータベースを縮小する必要があります。 詳細については、「[Manage file space in Azure SQL Database](sql-database-file-space-management.md)」(Azure SQL Database でファイル領域を管理する) を参照してください。


## <a name="single-database-storage-sizes-and-performance-levels"></a>単一データベース: ストレージ サイズとパフォーマンス レベル

次の表では、各サービス レベルおよびパフォーマンス レベルにおいて単一データベースで使用可能なリソースを示します。 [Azure Portal](sql-database-single-databases-manage.md#azure-portal-manage-logical-servers-and-databases)、[Transact-SQL](sql-database-single-databases-manage.md#transact-sql-manage-logical-servers-and-databases)、[PowerShell](sql-database-single-databases-manage.md#powershell-manage-logical-servers-and-databases)、[Azure CLI](sql-database-single-databases-manage.md#azure-cli-manage-logical-servers-and-databases)、または [REST API](sql-database-single-databases-manage.md#rest-api-manage-logical-servers-and-databases) を使って、単一のデータベースにサービス レベル、パフォーマンス レベル、ストレージ量を設定できます。

### <a name="general-purpose-service-tier"></a>汎用のサービス階層

#### <a name="generation-4-compute-platform"></a>第 4 世代コンピューティング プラットフォーム
|パフォーマンス レベル|GP_Gen4_1|GP_Gen4_2|GP_Gen4_4|GP_Gen4_8|GP_Gen4_16|GP_Gen4_24
|:--- | --: |--: |--: |--: |--: |--: |
|H/W の世代|4|4|4|4|4|4|
|仮想コア|1|2|4|8|16|24|
|メモリ (GB)|7|14|28|56|112|168|
|列ストアをサポート|はい|はい|はい|はい|はい|[はい]|
|インメモリ OLTP ストレージ (GB)|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|ストレージの種類|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|
|IO 待機時間 (概算)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|
|最大データ サイズ (GB)|1024|1024|1536|3072|4096|4096|
|最大ログ サイズ|307|307|461|922|1229|1229|
|TempDB のサイズ (GB)|32|64|128|256|384|384|
|ターゲットの IOPS (64 KB)|500|1,000|2000|4000|7000|7000|
|最大同時実行ワーカー (要求) 数|200|400|800|1600|3200|4800|
|許可される最大セッション数|30000|30000|30000|30000|30000|30000|
|レプリカの数|1|1|1|1|1|1|
|マルチ AZ|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|000
|読み取りスケールアウト|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|含まれるバックアップ ストレージ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|
|||

#### <a name="generation-5-compute-platform"></a>第 5 世代コンピューティング プラットフォーム
|パフォーマンス レベル|GP_Gen5_2|GP_Gen5_4|GP_Gen5_8|GP_Gen5_16|GP_Gen5_24|GP_Gen5_32|GP_Gen5_40| GP_Gen5_80|
|:--- | --: |--: |--: |--: |---: | --: |--: |--: |--: |
|H/W の世代|5|5|5|5|5|5|5|
|仮想コア|2|4|8|16|24|32|40|80|
|メモリ (GB)|11|22|44|88|132|176|220|440|
|列ストアをサポート|はい|はい|はい|はい|はい|はい|はい|[はい]|
|インメモリ OLTP ストレージ (GB)|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|ストレージの種類|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|Premium (リモート) ストレージ|
|IO 待機時間 (概算)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|5 ～ 7 ミリ秒 (書き込み)<br>5 ～ 10 ミリ秒 (読み取り)|
|最大データ サイズ (GB)|1024|1024|1536|3072|4096|4096|4096|4096|
|最大ログ サイズ|307|307|461|614|1229|1229|1229|1229|
|TempDB のサイズ (GB)|64|128|256|384|384|384|384|384|
|ターゲットの IOPS (64 KB)|500|1,000|2000|4000|6000|7000|7000|7000|
|最大同時実行ワーカー (要求) 数|200|400|800|1600|2400|3200|4000|8000|
|許可される最大セッション数|30000|30000|30000|30000|30000|30000|30000|30000|
|レプリカの数|1|1|1|1|1|1|1|1|
|マルチ AZ|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|読み取りスケールアウト|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|含まれるバックアップ ストレージ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|
|||

### <a name="business-critical-service-tier"></a>Business Critical サービス レベル

#### <a name="generation-4-compute-platform"></a>第 4 世代コンピューティング プラットフォーム
|パフォーマンス レベル|BC_Gen4_1|BC_Gen4_2|BC_Gen4_4|BC_Gen4_8|BC_Gen4_16|BC_Gen4_24|
|:--- | --: |--: |--: |--: |--: |--: |
|H/W の世代|4|4|4|4|4|4|
|仮想コア|1|2|4|8|16|24|
|メモリ (GB)|7|14|28|56|112|168|
|列ストアをサポート|はい|はい|はい|はい|はい|[はい]|
|インメモリ OLTP ストレージ (GB)|1|2|4|8|20|36|
|ストレージの種類|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|
|最大データ サイズ (GB)|1024|1024|1024|1024|1024|1024|
|最大ログ サイズ|307|307|307|307|307|307|
|TempDB のサイズ (GB)|32|64|128|256|384|384|
|ターゲットの IOPS (64 KB)|5000|10000|20000|40000|80000|120000|
|IO 待機時間 (概算)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|
|最大同時実行ワーカー (要求) 数|200|400|800|1600|3200|4800|
|許可される最大セッション数|30000|30000|30000|30000|30000|30000|
|レプリカの数|3|3|3|3|3|3|
|マルチ AZ|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|読み取りスケールアウト|[はい]|はい|はい|はい|はい|[はい]|
|含まれるバックアップ ストレージ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|
|||

#### <a name="generation-5-compute-platform"></a>第 5 世代コンピューティング プラットフォーム
|パフォーマンス レベル|BC_Gen5_2|BC_Gen5_4|BC_Gen5_8|BC_Gen5_16|BC_Gen5_24|BC_Gen5_32|BC_Gen5_40|BC_Gen5_80|
|:--- | --: |--: |--: |--: |---: | --: |--: |--: |--: |--: |--: |--: |--: |
|H/W の世代|5|5|5|5|5|5|5|5|
|仮想コア|2|4|8|16|24|32|40|80|
|メモリ (GB)|11|22|44|88|132|176|220|440|
|列ストアをサポート|はい|はい|はい|はい|はい|はい|はい|[はい]|
|インメモリ OLTP ストレージ (GB)|1.571|3.142|6.284|15.768|25.252|37.936|52.22|131.64|
|ストレージの種類|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|ローカル SSD|
|IO 待機時間 (概算)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|1 ～ 2 ミリ秒 (書き込み)<br>1 ～ 2 ミリ秒 (読み取り)|
|最大データ サイズ (GB)|1024|1024|1024|1024|2048|4096|4096|4096|
|最大ログ サイズ|307|307|307|307|614|1229|1229|1229|
|TempDB のサイズ (GB)|64|128|256|384|384|384|384|384|
|ターゲットの IOPS (64 KB)|5000|10000|20000|40000|60000|80000|100000|200000
|最大同時実行ワーカー (要求) 数|200|400|800|1600|2400|3200|4000|8000|
|許可される最大セッション数|30000|30000|30000|30000|30000|30000|30000|30000|
|レプリカの数|3|3|3|3|3|3|3|3|
|マルチ AZ|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|読み取りスケールアウト|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|該当なし|
|含まれるバックアップ ストレージ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|1X DB サイズ|
|||

## <a name="next-steps"></a>次の手順

- よく寄せられる質問の回答については、「[SQL Database に関する FAQ](sql-database-faq.md)」を参照してください。
- Azure の一般的な制限については、「[Azure サブスクリプションとサービスの制限、クォータ、制約](../azure-subscription-service-limits.md)」をご覧ください。

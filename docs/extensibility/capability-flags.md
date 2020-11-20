---
title: Yetenek bayrakları | Microsoft Docs
description: Kaynak denetim eklentisinin yeteneklerini ve genişletilmiş özellikleri belirten SCC_EXCAP_xxx bayraklarını belirten SCC_CAP_xxx bayrakları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b80672b00bec95c740824ef7e29f1faba0e63cf4
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974443"
---
# <a name="capability-flags"></a>Yetenek bayrakları
SCC_CAP_ *XXX* bayrakları, kaynak denetimi eklentisinin yeteneklerini göstermek için kullanılan bit bayraklardır. SCC_EXCAP_ *XXX* bayrakları, genişletilmiş özellikleri belirten ve tamsayı değerlerine çözümleyecek artımlı bayraklardır.

|Yetenek kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|[SccRemove](../extensibility/sccremove-function.md) ve komutunu destekler.|
|`SCC_CAP_RENAME`|0x00000002L|[SccRename](../extensibility/sccrename-function.md) ve komutunu destekler.|
|`SCC_CAP_DIFF`|0x00000004L|[SccDiff](../extensibility/sccdiff-function.md) ve komutunu destekler.|
|`SCC_CAP_HISTORY`|0x00000008L|[SccHistory](../extensibility/scchistory-function.md) ve komutunu destekler.|
|`SCC_CAP_PROPERTIES`|0x00000010L|[SccProperties](../extensibility/sccproperties-function.md) ve komutunu destekler.|
|`SCC_CAP_RUNSCC`|0x00000020L|[SccRunScc](../extensibility/sccrunscc-function.md) ve komutunu destekler.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|[Sccgetcommandoçenve](../extensibility/sccgetcommandoptions-function.md) komutunu destekler.|
|`SCC_CAP_QUERYINFO`|0x00000080L|[SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve komutunu destekler.|
|`SCC_CAP_GETEVENTS`|0x00000100L|[SccGetEvents](../extensibility/sccgetevents-function.md) ve komutunu destekler.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|[SccGetProjPath](../extensibility/sccgetprojpath-function.md) ve komutunu destekler.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|[SccAddFromScc](../extensibility/sccaddfromscc-function.md) ve komutunu destekler.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Kullanıma alma sırasında yorumu destekler.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|İade sırasında yorumu destekler.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Add ile ilgili yorumu destekler.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Kaldırma sırasında bir yorumu destekler.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Metni IDE tarafından sağlanmış bir çıkış işlevine yazar.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|, Deltas olmadan dosya depolamayı destekler.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Birden çok dosya geçmişini destekler.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Büyük/küçük harf duyarsız dosya karşılaştırmayı destekler.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Boşluğu yok sayan dosya karşılaştırmayı destekler.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Ek dosya bulmayı destekler.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Proje oluşturma hakkındaki açıklamaları destekler.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Denetim altında tüm durumlarda farkı destekler.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Eklenti Get için bir kullanıcı arabirimini desteklemez, ancak IDE, [SccGet](../extensibility/sccget-function.md)çağrısını hala çağırabilir.|
|`SCC_CAP_REENTRANT`|0x40000000L|Eklenti yeniden ve iş parçacığı açısından güvenlidir. Sürüm 1,0 ' de, yeniden Eklenme ve iş parçacığı güvenli olarak hiçbir eklentinin kabul edildiği varsayılmadı. Bir 1,1 eklentisi bu biti ayarlarsa, konağın birden fazla projeyi paralel olarak açmasına izin verilir.|

## <a name="capability-bits-added-in-version-12"></a>Sürüm 1,2 ' de özellik bitleri eklendi

|Yetenek kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|[Scccreatealt projesini](../extensibility/scccreatesubproject-function.md)destekler.|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)'i destekler.|
|`SCC_CAP_BATCH`|0x00040000L|[SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve [SccEndBatch](../extensibility/sccendbatch-function.md)' i destekler.|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|, [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)destekler.|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|, [SccDirDiff](../extensibility/sccdirdiff-function.md)destekler.|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|, Bir dosyada birden çok kullanıma almayı destekler ve [Sccımulticheckoutenabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|*Mssccprj. SCC* dosyasını (Kullanıcı/yönetici geçersiz kılma 'ya tabi) ve [Sccwillcreatesccdosyasına](../extensibility/sccwillcreatesccfile-function.md)destekler.|

## <a name="capability-bits-added-in-version-13"></a>Sürüm 1,3 ' de özellik bitleri eklendi
 Bu bayraklar, özelliğin desteklenip desteklenmediğini anlamak için bir seferde [Sccgeetdedcapabilities](../extensibility/sccgetextendedcapabilities-function.md) işlevine geçirilir.

|Genişletilmiş yetenek kodu|Değer|Açıklama|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Kullanıma alma `SCC_CHECKOUT_LOCALVER` seçeneğini destekler.|
|`SCC_EXCAP_BACKGROUND_GET`|2|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)'i destekler.|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|[Sccenumchangeddosyalarını](../extensibility/sccenumchangedfiles-function.md)destekler.|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Ek dizinlerin bulunmasını destekler.|
|`SCC_EXCAP_QUERYCHANGES`|5|Dosya değişikliklerinin numaralandırılması destekler.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)' i destekler.|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)'i destekler.|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Birden çok iş parçacığında SccQueryInfo çağrılmasını destekler.|
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir işlevini destekler.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|, Kullanıma alınmış dosyaları silebilir.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|, Kullanıma alınmış dosyaları yeniden adlandırabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)

---
title: Yetenek Bayrakları | Microsoft Docs
description: Kaynak denetimi SCC_CAP_xxx özelliklerini gösteren bayraklar ve genişletilmiş özellikleri gösteren SCC_EXCAP_xxx bayrakları hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdb660fd4e7c595f522686280f8bec6c0acae81
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905104"
---
# <a name="capability-flags"></a>Yetenek bayrakları
Xxx *SCC_CAP_,* bir kaynak denetim eklentisinin özelliklerini belirtmek için kullanılan bit bayraklarıdır. Xxx *SCC_EXCAP_, genişletilmiş* özellikleri gösteren ve tamsayı değerlerine çözümlene artımlı bayraklardır.

|Yetenek Kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|[SccRemove ve](../extensibility/sccremove-function.md) komutunu destekler.|
|`SCC_CAP_RENAME`|0x00000002L|[SccRename ve komutunu](../extensibility/sccrename-function.md) destekler.|
|`SCC_CAP_DIFF`|0x00000004L|[SccDiff ve komutunu](../extensibility/sccdiff-function.md) destekler.|
|`SCC_CAP_HISTORY`|0x00000008L|[SccHistory ve komutunu](../extensibility/scchistory-function.md) destekler.|
|`SCC_CAP_PROPERTIES`|0x00000010L|[SccProperties ve komutunu](../extensibility/sccproperties-function.md) destekler.|
|`SCC_CAP_RUNSCC`|0x00000020L|[SccRunScc ve komutunu](../extensibility/sccrunscc-function.md) destekler.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|[SccGetCommandOptions ve](../extensibility/sccgetcommandoptions-function.md) komutunu destekler.|
|`SCC_CAP_QUERYINFO`|0x00000080L|[SccQueryInfo ve komutunu](../extensibility/sccqueryinfo-function.md) destekler.|
|`SCC_CAP_GETEVENTS`|0x00000100L|[SccGetEvents ve](../extensibility/sccgetevents-function.md) komutunu destekler.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|[SccGetProjPath ve komutunu](../extensibility/sccgetprojpath-function.md) destekler.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|[SccAddFromScc ve komutunu](../extensibility/sccaddfromscc-function.md) destekler.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Geri alma ile ilgili bir açıklamayı destekler.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Iade ile ilgili bir açıklamayı destekler.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Ekle ile ilgili bir açıklamayı destekler.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Kaldır ile ilgili bir açıklamayı destekler.|
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE tarafından sağlanan bir çıkış işlevine metin yazar.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Dosyaları delta olmadan depolamayı destekler.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Birden çok dosya geçmişini destekler.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Büyük/büyük/büyük harfe duyarlı olmayan dosya karşılaştırmayı destekler.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Boş alanı yoksayan dosya karşılaştırmayı destekler.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Ek dosyaları bulmayı destekler.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Proje oluşturma ile ilgili yorumları destekler.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Denetim altında ise tüm eyaletlerde farkları destekler.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Eklenti Get için bir kullanıcı arabirimini desteklemez, ancak IDE yine de [SccGet çağrısında olabilir.](../extensibility/sccget-function.md)|
|`SCC_CAP_REENTRANT`|0x40000000L|Eklenti yeniden ve iş parçacığı güvenlidir. Sürüm 1.0'da, hiçbir eklentinin yeniden kabul edildi ve iş parçacığı güvenli olduğu varsayıldı. Bir 1.1 eklentisi bu biti ayarlarsa, ana bilgisayar birden çok projeyi paralel olarak açmasına izin verilir.|

## <a name="capability-bits-added-in-version-12"></a>Sürüm 1.2'ye özellik bitleri eklendi

|Yetenek Kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|[SccCreateSubProject'i destekler.](../extensibility/scccreatesubproject-function.md)|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|[SccGetParentProjectPath'i destekler.](../extensibility/sccgetparentprojectpath-function.md)|
|`SCC_CAP_BATCH`|0x00040000L|[SccBeginBatch ve](../extensibility/sccbeginbatch-function.md) [SccEndBatch'i destekler.](../extensibility/sccendbatch-function.md)|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|[SccDirQueryInfo destekler.](../extensibility/sccdirqueryinfo-function.md)|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|[SccDirDiff'i destekler.](../extensibility/sccdirdiff-function.md)|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Bir dosyada birden çok iadeyi ve [SccIsMultiCheckoutEnabled'i destekler.](../extensibility/sccismulticheckoutenabled-function.md)|
|`SCC_CAP_SCCFILE`|0x80000000L|*MSSCCPRJ.SCC dosyasını* (kullanıcı/yönetici geçersiz kılmaya tabi) ve [SccWillCreateSccFile'ı destekler.](../extensibility/sccwillcreatesccfile-function.md)|

## <a name="capability-bits-added-in-version-13"></a>Sürüm 1.3'e özellik bitleri eklendi
 Bu bayraklar, özelliğin desteksiz olup olmadığını belirlemek için [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) işlevine tek tek geçirılır.

|Genişletilmiş Yetenek Kodu|Değer|Açıklama|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Satın `SCC_CHECKOUT_LOCALVER` almalar için seçeneğini destekler.|
|`SCC_EXCAP_BACKGROUND_GET`|2|[SccBackgroundGet'i destekler.](../extensibility/sccbackgroundget-function.md)|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|[SccEnumChangedFiles'i destekler.](../extensibility/sccenumchangedfiles-function.md)|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Ek dizinleri bulmayı destekler.|
|`SCC_EXCAP_QUERYCHANGES`|5|Dosya değişikliklerinin numaralarını destekleme.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|[SccAddFilesFromSCC destekler.](../extensibility/sccaddfilesfromscc-function.md)|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|[SccGetUserOption destekler.](../extensibility/sccgetuseroption-function.md)|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Birden çok iş parçacığında SccQueryInfo çağırmayı destekler.|
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir işlevini destekler.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|, Kullanıma alınmış dosyaları silebilir.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|, Kullanıma alınmış dosyaları yeniden adlandırabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)

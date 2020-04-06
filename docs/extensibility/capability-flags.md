---
title: Yetenek Bayrakları | Microsoft Dokümanlar
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
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739875"
---
# <a name="capability-flags"></a>Yetenek bayrakları
SCC_CAP_*xxx* bayrakları, kaynak denetimi eklentisinin yeteneklerini belirtmek için kullanılan bit bayraklarıdır. SCC_EXCAP_*xxx* bayrakları genişletilmiş yetenekleri gösteren ve tamsayı değerlerine çözümleyen artımlı bayraklardır.

|Yetenek Kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|[SccRemove](../extensibility/sccremove-function.md) ve komutunu destekler.|
|`SCC_CAP_RENAME`|0x0000002L|[SccRename](../extensibility/sccrename-function.md) ve komutunu destekler.|
|`SCC_CAP_DIFF`|0x00000004L|[SccDiff](../extensibility/sccdiff-function.md) ve komutunu destekler.|
|`SCC_CAP_HISTORY`|0x0000008L|[SccHistory](../extensibility/scchistory-function.md) ve komutunu destekler.|
|`SCC_CAP_PROPERTIES`|0x00000010L|[SccProperties](../extensibility/sccproperties-function.md) ve komutunu destekler.|
|`SCC_CAP_RUNSCC`|0x00000020L|[SccRunScc](../extensibility/sccrunscc-function.md) ve komutunu destekler.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) ve komutunu destekler.|
|`SCC_CAP_QUERYINFO`|0x00000080L|[SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve komutunu destekler.|
|`SCC_CAP_GETEVENTS`|0x00000100L|[SccGetEvents](../extensibility/sccgetevents-function.md) ve komutunu destekler.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|[SccGetProjPath](../extensibility/sccgetprojpath-function.md) ve komutunu destekler.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|[SccAddFromScc](../extensibility/sccaddfromscc-function.md) ve komutunu destekler.|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Ödeme yle ilgili bir yorumu destekler.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|İade ile ilgili bir yorumu destekler.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Ekle hakkındaki bir yorumu destekler.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Kaldır'la ilgili bir yorumu destekler.|
|`SCC_CAP_TEXTOUT`|0x00008000L|IDE tarafından sağlanan bir çıktı işlevine metin yazar.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Dosyaları deltaolmadan depolamayı destekler.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Birden çok dosya geçmişini destekler.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Büyük/küçük harf duyarsız dosya karşılaştırmadestekler.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Beyaz alanı yoksayan dosya karşılaştırması destekler.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Ek dosyaların bulunmasını destekler.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Proje oluşturma hakkındaki açıklamaları destekler.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Denetim altındaysa tüm eyaletlerde diff'i destekler.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Eklenti Get için bir UI desteklemez, ancak IDE hala [SccGet](../extensibility/sccget-function.md)arayabilirsiniz.|
|`SCC_CAP_REENTRANT`|0x40000000L|Eklenti reentrant ve iş parçacığı güvenlidir. Sürüm 1.0'da, hiçbir eklentinin reentrant ve iş parçacığı güvenli olduğu varsayılmıştır. 1.1 eklentisi bu biti ayarlarsa, ana bilgisayar paralel olarak birden çok proje açabilir.|

## <a name="capability-bits-added-in-version-12"></a>Sürüm 1.2'ye eklenen yetenek bitleri

|Yetenek Kodu|Değer|Açıklama|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|[SccCreateSubProject'i](../extensibility/scccreatesubproject-function.md)destekler.|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)destekler.|
|`SCC_CAP_BATCH`|0x00040000L|[SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve [SccEndBatch](../extensibility/sccendbatch-function.md)destekler.|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)destekler.|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|[SccDirDiff](../extensibility/sccdirdiff-function.md)destekler.|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Bir dosya ve [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)üzerinde birden çok ödeme destekler.|
|`SCC_CAP_SCCFILE`|0x80000000L|*MSSCCPRJ.SCC* dosyasını (kullanıcı/yönetici geçersiz kılmaya tabidir) ve [SccWillCreateSccFile'ı](../extensibility/sccwillcreatesccfile-function.md)destekler.|

## <a name="capability-bits-added-in-version-13"></a>Sürüm 1.3'e eklenen yetenek bitleri
 Bu bayraklar, yeteneğin desteklenip desteklenmediğini belirlemek için [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) işlevine birer birer geçirilir.

|Genişletilmiş Yetenek Kodu|Değer|Açıklama|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Ödeme `SCC_CHECKOUT_LOCALVER` seçeneğini destekler.|
|`SCC_EXCAP_BACKGROUND_GET`|2|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)destekler.|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)destekler.|
|`SCC_EXCAP_POPULATELIST_DIR`|4|İlave dizinbulmayı destekler.|
|`SCC_EXCAP_QUERYCHANGES`|5|Dosya değişikliklerini ayırmayı destekler.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)destekler.|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)destekler.|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Birden çok iş parçacığı üzerinde SccQueryInfo arama destekler.|
|`SCC_EXCAP_REMOVE_DIR`|9|SccRemoveDir işlevini destekler.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Kullanıma alınan dosyaları silebilir.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Kullanıma alınan dosyaları yeniden adlandırabilir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)

---
title: Kaynak Denetimi Eklentisi API İşlevleri | Microsoft Docs
description: Kaynak Denetimi Eklentisi API'sinde bulunan ve kaynak denetimi eklentisi tarafından uygulanması gereken işlevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 369acd0f0b459aa4d5e5691c0159087c0bdf152edeb5388d3f62d3978f58ac30
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431467"
---
# <a name="source-control-plug-in-api-functions"></a>Kaynak Denetimi Eklentisi API İşlevleri
Kaynak Denetimi Eklentisi API'si, kaynak denetimi eklentisi tarafından bu API'ye uygun olarak uygulanması gereken aşağıdaki işlevleri sağlar. Her işlevin imzaları ve bit bayrakları ve diğer parametrelerle ilişkili semantikler bu başvuruda ayrıntılı olarak açıklanmıştır.

## <a name="initialization-and-housekeeping-functions"></a>Başlatma ve Bakım İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Projeyi kapatır.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Kullanıcıdan verilen komut için gelişmiş seçenekler istenir.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Kaynak denetimi eklentisinin sürümünü döndürür.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Kaynak denetimi eklentiyi başlatılır. Eklentinin her örneği için bir kez çağrılır.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Bir proje açar.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Çok çeşitli seçenekler ayarlamak için kullanılan genel bir işlev. Her seçenek ile `SCC_OPT_xxx` başlar ve kendi tanımlı değer kümesine sahiptir.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Kaynak denetimi eklentisinin kablolarının açık olması gerekirken bir kez çağrılır.|

## <a name="core-source-control-functions"></a>Çekirdek Kaynak Denetimi İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Kaynak denetim sistemine tam yol adları tarafından belirtilen bir dosya dizisi ekler.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Kullanıcının kaynak denetim sisteminde zaten bulunan dosyalara göz atarak bu dosyaları geçerli projenin parçası yapmalarına izin verir.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Bir dosya dizisini denetler.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Bir dosya dizisini denetler.|
|[SccDiff](../extensibility/sccdiff-function.md)|Yerel kullanıcının tam yol adı ile kaynak denetimi altındaki sürüm tarafından belirtilen dosyası arasındaki farkları gösterir.|
|[SccGet](../extensibility/sccget-function.md)|Bir dosya kümesi için salt okunur bir kopyayı alan.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Çağıranın sorarak sortt olduğu dosyaların durumunu denetler `SccQueryInfo` (aracılığıyla).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Kaynak denetimi eklentisinin kullanıcıdan eklenti için anlamlı bir proje yolu isteminde uzlatır.|
|[SccHistory](../extensibility/scchistory-function.md)|Tam yerel dosya adları dizisinin geçmişini gösterir.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Geçerli durumları için dosya listesini inceler. Ayrıca, bir dosya `pfnPopulate` ölçütüyle eşleşmezken çağıranı bildirmek için işlevini `nCommand` kullanır.|
|[SccProperties](../extensibility/sccproperties-function.md)|Tam dosyanın özelliklerini gösterir.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Geçerli durumları için tam dosya listesini inceler.|
|[SccRemove](../extensibility/sccremove-function.md)|Kaynak denetim sisteminden tam dosya dizisini kaldırır.|
|[SccRename](../extensibility/sccrename-function.md)|Verilen dosyayı kaynak denetim sisteminde yeni bir adla yeniden adlandırır.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Kaynak denetim sisteminin tüm özelliklerine erişer.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Bir dosya dizisinin kullanıma alma işlemini geri döndürür.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Ek Özelliği Destekleyen İşlevler (Kaynak Denetimi Eklentisi API'sinde Sürüm 1.2)
 Bu işlev grubu, Kaynak Denetimi Eklentisi API'sini 1.2 sürümüne dahil edilen ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Toplu işlem başlatır.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Mevcut bir üst proje altında verilen adla bir alt proje oluşturur.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Tam yol adı ile kaynak denetimi veritabanı konumu tarafından belirtilen yerel kullanıcının dizini arasındaki farkları gösterir.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Geçerli durumları için tam dizinlerin listesini inceler.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Toplu işlemi sonlar.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Belirtilen projenin üst yolunu döndürür (projenin mevcut olması gerekir).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Bir dosyada birden çok iadeye izin verili olup olmadığını denetler.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Eklentinin MSSCCPRJ oluşturıp oluşturmayacaklarını denetler. SCC dosyaları.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Gelişmiş Özelliği Destekleyen İşlevler (Kaynak Denetimi Eklentisi API'sinde Sürüm 1.3)
 Bu işlev grubu, Kaynak Denetimi Eklentisi API'sini 1.3 sürümüne dahil edilen ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Kaynak denetiminden geçerli projeye dosya listesi ekler.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Kaynak denetiminden kullanıcı arabirimi olmadan dosyaların listesini alan.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Kaynak denetiminde yerel dosyalardan farklı dosyaların listesini alan.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Kaynak denetimi eklentisi tarafından desteklenen genişletilmiş özellikleri belirten bayrakları alın.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçenekleri alma.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Bir proje veya proje içinde kaynak denetimi altında olan dizinlerin ve dosyaların listesini inceler. Bulunan her dizin ve dosya adı bir geri çağırma işlevine geçirildi.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Dosya listesinde yapılan ad değişikliklerini inceler. Her dosya adı, değişiklik durumuyla bir geri çağırma işlevine geçirilir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SCC. h

 (Varsayılan *[sürücü]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc; ADLı ortam SDK ortak içerme klasörü, MSSCCI örneği, *[sürücü]* \Program Files\VSIP 8.0 \ MSSCCı) ile VSIP klasöründe de sağlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)

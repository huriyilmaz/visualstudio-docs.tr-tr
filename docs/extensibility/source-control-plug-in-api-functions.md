---
title: Kaynak denetimi eklentisi API Işlevleri | Microsoft Docs
description: Kaynak denetimi eklentisi API 'sinin sağladığı ve kaynak denetimi eklentisi tarafından uygulanması gereken işlevler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c28c175d53fb37cf890dad4240a84fb132f6af35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090128"
---
# <a name="source-control-plug-in-api-functions"></a>Kaynak Denetimi Eklentisi API İşlevleri
Kaynak denetimi eklentisi API 'si, bu API 'ye uygun olarak kaynak denetimi eklentisi tarafından uygulanması gereken aşağıdaki işlevleri sağlar. Her bir işlevin imzaları ve bit bayraklarıyla ve diğer parametrelerle ilişkili semantik bu başvuruda ayrıntılı olarak açıklanmaktadır.

## <a name="initialization-and-housekeeping-functions"></a>Başlatma ve temizlik Işlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Bir projeyi kapatır.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Kullanıcıdan verilen komutla ilgili gelişmiş seçenekleri ister.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Kaynak denetimi eklentisinin sürümünü döndürür.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Kaynak denetimi eklentisini başlatır. Bu, eklentinin her örneği için bir kez çağrılır.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Bir proje açar.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Çok çeşitli seçenekler ayarlamak için kullanılan genel bir işlev. Her seçenek ile başlar `SCC_OPT_xxx` ve kendi tanımlı değer kümesine sahiptir.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Kaynak denetim eklentisinin sökülilmesi gerektiğinde çağrılır.|

## <a name="core-source-control-functions"></a>Çekirdek kaynak denetim Işlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Kaynak denetim sistemine tam nitelikli yol adları tarafından belirtilen bir dosya dizisi ekler.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Kullanıcının zaten kaynak denetimi sisteminde olan dosyalara gözatmasına ve ardından bu dosyaları geçerli projenin bir parçası haline getirir.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Bir dosya dizisinde denetim gerçekleştirir.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Bir dizi dosyayı kontrol eder.|
|[SccDiff](../extensibility/sccdiff-function.md)|Yerel kullanıcının dosyası ile tam nitelikli yol adı ve kaynak denetimi altındaki sürüm arasındaki farkları gösterir.|
|[SccGet](../extensibility/sccget-function.md)|Bir dosya kümesinin salt okunurdur kopyasını alır.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Çağıranın hakkında istediği dosyaların durumunu denetler (aracılığıyla `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Kaynak denetimi eklentisinin, kullanıcıdan eklentiye anlamlı bir proje yolu sorması için izin vermesine neden olur.|
|[SccHistory](../extensibility/scchistory-function.md)|Tam olarak nitelenmiş yerel dosya adları dizisinin geçmişini gösterir.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Geçerli durumları için dosya listesini inceler. Ayrıca, `pfnPopulate` bir dosya ile ilgili ölçütlerle eşleşmediği zaman, çağrıyı yapana bildirmek için işlevini kullanır `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Tam nitelikli bir dosyanın özelliklerini gösterir.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Geçerli durumları için tam olarak nitelenmiş dosyaların bir listesini inceler.|
|[SccRemove](../extensibility/sccremove-function.md)|Kaynak denetim sisteminden tam nitelikli dosya dizisini kaldırır.|
|[SccRename](../extensibility/sccrename-function.md)|Verilen dosyayı kaynak denetim sistemindeki yeni bir adla yeniden adlandırır.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Kaynak denetim sisteminin tüm özelliklerine erişir.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Bir dosya dizisinin kullanıma alınmasını geri alır.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Ek özelliği destekleyen işlevler (kaynak denetimi eklentisi API 'sinin sürüm 1,2)
 Bu işlev grubu, kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de yer alan ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Bir toplu işlem başlatır.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Varolan bir üst proje altında verilen ada sahip bir alt proje oluşturur.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Bir tam yol adı ve kaynak denetimi veritabanı konumu tarafından belirtilen yerel kullanıcının dizini arasındaki farkları gösterir.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Geçerli durumları için tam dizinlerin listesini inceler.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Toplu işlemi sonlandırır.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Verilen projenin üst yolunu döndürür (projenin mevcut olması gerekir).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Bir dosyada birden fazla kullanıma alma yapılmasına izin verilip verilmediğini denetler.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Eklentinin MSSCCPRJ oluşturup oluşturmayacağını denetler. SCC dosyaları.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Gelişmiş özelliği destekleyen işlevler (kaynak denetimi eklentisi API 'sinin sürüm 1,3)
 Bu işlev grubu, kaynak denetimi eklentisi API 'sinin sürüm 1,3 ' de yer alan ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Kaynak denetiminden geçerli projeye dosya listesi ekler.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Kaynak denetiminden bir kullanıcı arabirimi olmadan dosyaların listesini alır.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Kaynak denetimindeki dosyaların listesini yerel dosyalardan farklı bir şekilde alır.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Kaynak denetimi eklentisi tarafından desteklenen genişletilmiş özellikleri belirten bayrakları alır.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Kullanıcıya özel seçenekleri alır.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Kaynak denetimi altındaki bir projedeki veya projelerdeki dizinlerin ve dosyaların listesini inceler. Bulunan her dizin ve dosya adı bir geri çağırma işlevine geçirilir.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Dosya listesinde yapılan ad değişikliklerini inceler. Her dosya adı, değişiklik durumuyla bir geri çağırma işlevine geçirilir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SCC. h

 (Varsayılan *[sürücü]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc; ADLı ortam SDK ortak içerme klasörü, MSSCCI örneği, *[sürücü]* \Program Files\VSIP 8.0 \ MSSCCı) ile VSIP klasöründe de sağlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)

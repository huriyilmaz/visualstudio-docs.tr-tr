---
title: Kaynak Kontrol Eklentisi API Fonksiyonları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699918"
---
# <a name="source-control-plug-in-api-functions"></a>Kaynak Denetimi Eklentisi API İşlevleri
Kaynak Denetim Eklentisi API, bu API uyarınca kaynak denetim eklentisi tarafından uygulanması gereken aşağıdaki işlevleri sağlar. Her işlevin imzaları ve bit bayrakları ve diğer parametrelerle ilişkili anlamsallar bu başvuruda ayrıntılı olarak açıklanmıştır.

## <a name="initialization-and-housekeeping-functions"></a>Başlatma ve Temizlik Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Bir projeyi kapatır.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Verilen komut için gelişmiş seçenekler için kullanıcı ister.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Kaynak denetim eklentisinin sürümünü döndürür.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Kaynak kontrol eklentisini başolarak karşılar. Eklentinin her örneği için bir kez çağrılır.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Bir proje açar.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Çok çeşitli seçenekler ayarlamak için kullanılan genel bir işlev. Her seçenek `SCC_OPT_xxx` ile başlar ve kendi tanımlanmış değerler kümesi vardır.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Kaynak kontrol eklentisi fişinin çıkarılması gerektiğinde bir kez çağrılır.|

## <a name="core-source-control-functions"></a>Çekirdek Kaynak Kontrol Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Kaynak denetim sistemine tam nitelikli yol adları tarafından belirtilen bir dizi dosya ekler.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Kullanıcının kaynak denetim sisteminde bulunan dosyalara göz atmasını ve ardından bu dosyaları geçerli projenin bir parçası haline getirmesini sağlar.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Bir dizi dosyayı denetler.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Bir dizi dosyayı kontrol eder.|
|[SccDiff](../extensibility/sccdiff-function.md)|Yerel kullanıcının dosyası ile tam nitelikli bir yol adı tarafından belirtilen dosya arasındaki farkları gösterir ve kaynak denetimi altındaki sürüm.|
|[SccGet](../extensibility/sccget-function.md)|Bir dosya kümesinin salt okunur kopyasını alır.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Arayanın sorduğu dosyaların durumunu denetler (üzerinden). `SccQueryInfo`|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Kaynak denetim eklentisinin kullanıcıdan eklenti için anlamlı bir proje yolu için istenmesine neden olur.|
|[SccHistory](../extensibility/scchistory-function.md)|Tam nitelikli yerel dosya adları dizisinin geçmişini gösterir.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Geçerli durumları için dosyaların listesini inceler. Buna ek olarak, bir dosya için ölçütleri eşleşmiyor zaman arayan bildirmek için `pfnPopulate` işlevi `nCommand`kullanır.|
|[SccProperties](../extensibility/sccproperties-function.md)|Tam nitelikli bir dosyanın özelliklerini gösterir.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Geçerli durumları için tam nitelikli dosyaların listesini inceler.|
|[SccRemove](../extensibility/sccremove-function.md)|Kaynak denetim sisteminden tam nitelikli dosya dizisini kaldırır.|
|[SccRename](../extensibility/sccrename-function.md)|Verilen dosyayı kaynak denetim sistemindeki yeni bir ada yeniden adlandırır.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Kaynak kontrol sisteminin tüm özelliklerine erişir.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Bir dizi dosyanın kullanıma geri ödemesini geri alır.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Ek Yeteneği Destekleyen Işlevler (Kaynak Denetimi Eklentisi API Sürümü 1.2)
 Bu işlev grubu, Kaynak Denetimi Eklentisi EKLENTIsi API'sinin sürüm 1.2'sinde yer alan ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Toplu iş bir işlem başlatır.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Varolan bir üst proje altında verilen adı içeren bir alt proje oluşturur.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Tam nitelikli bir yol adı ile kaynak denetimi veritabanı konumu tarafından belirtilen yerel kullanıcının dizini arasındaki farkları gösterir.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Geçerli durumları için tam nitelikli dizinlerin listesini inceler.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Toplu iş bir işlemi sona erdirer.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Verilen projenin ana yolunu döndürür (proje var olmalıdır).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Bir dosyada birden çok kullanıma izin verilip verilmediğini denetler.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Eklentinin MSSCCPRJ oluşturup oluşturmayacağını denetler. SCC dosyaları.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Gelişmiş Yeteneği Destekleyen Fonksiyonlar (Kaynak Denetimi Eklentisi API Sürümü 1.3)
 Bu işlev grubu, Kaynak Denetimi Eklentisi EKLENTIsi API'sinin sürüm 1.3'ünde yer alan ek işlevleri tanımlar. Daha gelişmiş kaynak denetimi özelliklerine ve özelliklerine erişim sağlar.

|İşlev|Açıklama|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Geçerli projeye kaynak denetiminden dosyaların listesini ekler.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Kullanıcı arabirimi olmadan kaynak denetiminden dosyaların listesini alır.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Yerel dosyalardan farklı kaynak denetiminde dosyaların listesini alır.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Kaynak denetimi eklentisi tarafından desteklenen genişletilmiş yetenekleri belirten bayrakları alır.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Kullanıcıya özel seçenekleri alır.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Kaynak denetimi altında olan proje veya projelerdeki dizin ve dosyaların listesini inceler. Bulunan her dizin ve dosya adı bir geri arama işlevine geçirilir.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Dosya listesinde yapılan ad değişikliklerini inceler. Her dosya adı, değiştirme durumu olan bir geri arama işlevine geçirilir.|

## <a name="requirements"></a>Gereksinimler
 Başlık: scc.h

 (Çevre SDK ortak verilen klasör, varsayılan *olarak [sürücü]* \Program Files\VSIP 8.0\EnvSDK\common\inc; ayrıca MSSCCI örneği ile VSIP klasöründe sağlanan, *[sürücü]* \Program Files\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri](../extensibility/source-control-plug-ins.md)
- [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)

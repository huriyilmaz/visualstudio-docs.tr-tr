---
title: XDCMake görevi | Microsoft Docs
description: MSBuild, xml belge açıklama dosyalarını bir .xml dosyasında birleştiren xml belge aracı xdcmake.exe kaydırmak için xdcmake görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (C++))
- MSBuild (C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a363068c1965d51f8a72de79a8d620d2414b58ebd70c94a923750c50dd421b3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427489"
---
# <a name="xdcmake-task"></a>XDCMake görevi

XML belge açıklaması (*. xdc*) dosyalarını bir *.xml* dosyasına birleştiren XML belge aracı 'nı (*xdcmake.exe*) sarmalanmış hale gelir.

 C++ kaynak kodunuzda belge açıklamaları sağladığınızda ve [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) derleyici seçeneğini kullanarak derlerseniz bir *. xdc* dosyası oluşturulur. Daha fazla bilgi için, bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference), [XML belge Oluşturucu aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve *xdcmake.exe* için komut satırı yardım seçeneği (**/?**).

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, *xdcmake.exe* aracı birkaç komut satırı seçeneğini destekler. Ek seçenekler, **/Old** komut satırı seçeneğini belirttiğinizde desteklenir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XDCMake** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalDocumentFile**|İsteğe bağlı **dize []** parametresi.<br /><br /> Birleştirilecek bir veya daha fazla ek *. xdc* dosyasını belirtir.<br /><br /> Daha fazla bilgi için [XML belge Oluşturucu aracı özellik sayfalarındaki](/cpp/build/reference/xml-document-generator-tool-property-pages) **ek belge dosyaları** açıklamasına bakın. Ayrıca, *xdcmake.exe* için **/Old** ve **/FS** komut satırı seçeneklerine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Diğer bir **XDCMake** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için, bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference), [XML belge Oluşturucu aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve *xdcmake.exe* için komut satırı yardımı (**/?**).|
|**DocumentLibraryDependencies**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true` ve geçerli projenin, çözümdeki bir statik kitaplık (*. lib*) projesine bağımlılığı varsa, bu kitaplık projesi için *. xdc* dosyaları geçerli proje için *.xml* dosya çıktısına dahil edilir.<br /><br /> Daha fazla bilgi için bkz. [XML belge Oluşturucu aracı özellik sayfalarındaki](/cpp/build/reference/xml-document-generator-tool-property-pages) **belge kitaplığı bağımlılıkları** açıklaması.|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılar. Varsayılan ad, işlenen ilk *. xdc* dosyasının adından türetilir.<br /><br /> Daha fazla bilgi için bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference)içindeki **/Out: \<filename>** Option. Ayrıca, *xdcmake.exe* için **/Old** ve **/fo** komut satırı seçeneklerine bakın.|
|**ProjectName**|İsteğe bağlı **dize** parametresi.<br /><br /> Geçerli projenin adı.|
|**Slakıold**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Varsa `true` , ek *xdcmake.exe* seçeneklerini sunar.<br /><br /> Daha fazla bilgi için, *xdcmake.exe* için **/Old** komut satırı seçeneğine bakın.|
|**Kaynaklar**|Gerekli `ITaskItem[]` parametre.<br /><br /> görevler tarafından tüketilen ve yayılan MSBuild kaynak dosya öğelerinin dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için, [XDCMake başvurusunda](/cpp/build/reference/xdcmake-reference) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
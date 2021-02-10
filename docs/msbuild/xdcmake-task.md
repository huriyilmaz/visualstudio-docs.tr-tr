---
title: XDCMake görevi | Microsoft Docs
description: MSBuild 'in, XML belge açıklama dosyalarını bir. xml dosyasına birleştiren xdcmake.exe XML belge aracını kaydırmak için XDCMake görevini nasıl kullandığını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 4a867146d48b5ba6c4bfb2ac33b45c505b6f6c37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971056"
---
# <a name="xdcmake-task"></a>XDCMake görevi

XML belge açıklaması (*. xdc*) dosyalarını bir *. XML* dosyasında birleştiren XML belge aracı 'nı (*xdcmake.exe*) sarmalanmış hale gelir.

 C++ kaynak kodunuzda belge açıklamaları sağladığınızda ve [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) derleyici seçeneğini kullanarak derlerseniz bir *. xdc* dosyası oluşturulur. Daha fazla bilgi için, bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference), [XML belge Oluşturucu aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve *xdcmake.exe* için komut satırı yardım seçeneği (**/?**).

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, *xdcmake.exe* aracı birkaç komut satırı seçeneğini destekler. Ek seçenekler, **/Old** komut satırı seçeneğini belirttiğinizde desteklenir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XDCMake** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalDocumentFile**|İsteğe bağlı **dize []** parametresi.<br /><br /> Birleştirilecek bir veya daha fazla ek *. xdc* dosyasını belirtir.<br /><br /> Daha fazla bilgi için [XML belge Oluşturucu aracı özellik sayfalarındaki](/cpp/build/reference/xml-document-generator-tool-property-pages) **ek belge dosyaları** açıklamasına bakın. Ayrıca, *xdcmake.exe* için **/Old** ve **/FS** komut satırı seçeneklerine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Diğer bir **XDCMake** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için, bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference), [XML belge Oluşturucu aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve *xdcmake.exe* için komut satırı yardımı (**/?**).|
|**DocumentLibraryDependencies**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`Ve geçerli projenin çözümde bir statik kitaplık (*. lib*) projesine bağımlılığı varsa, bu kitaplık projesi için *. xdc* dosyaları geçerli proje için *. xml* dosya çıktısına dahil edilir.<br /><br /> Daha fazla bilgi için bkz. [XML belge Oluşturucu aracı özellik sayfalarındaki](/cpp/build/reference/xml-document-generator-tool-property-pages) **belge kitaplığı bağımlılıkları** açıklaması.|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılar. Varsayılan ad, işlenen ilk *. xdc* dosyasının adından türetilir.<br /><br /> Daha fazla bilgi için bkz. [XDCMake başvurusu](/cpp/build/reference/xdcmake-reference)içindeki **/Out: \<filename>** Option. Ayrıca, *xdcmake.exe* için **/Old** ve **/fo** komut satırı seçeneklerine bakın.|
|**ProjectName**|İsteğe bağlı **dize** parametresi.<br /><br /> Geçerli projenin adı.|
|**Slakıold**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Varsa `true` , ek *xdcmake.exe* seçeneklerini sunar.<br /><br /> Daha fazla bilgi için, *xdcmake.exe* için **/Old** komut satırı seçeneğine bakın.|
|**Kaynaklar**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için, [XDCMake başvurusunda](/cpp/build/reference/xdcmake-reference) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
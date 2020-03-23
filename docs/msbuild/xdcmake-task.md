---
title: XDCMake Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c41bfc2015f29cbb73b33df3594b3a3430af3f3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630658"
---
# <a name="xdcmake-task"></a>XDCMake görevi

XML belge yorumunu (*.xdc*) dosyalarını bir *.xml* dosyasında birleştiren XML Dokümantasyon aracını *(xdcmake.exe)* sarar.

 C++ kaynak kodunuzda doküman açıklamaları verdiğinizde ve [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) derleyici seçeneğini kullanarak derlediğinizde bir *.xdc* dosyası oluşturulur. Daha fazla bilgi için, *xdcmake.exe*için [XDCMake referans](/cpp/build/reference/xdcmake-reference), [XML Belge Jeneratör Aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve komut satırı yardım seçeneği (**/?**) bakın.

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, *xdcmake.exe* aracı birkaç komut satırı seçeneğini destekler. **/eski** komut satırı seçeneğini belirttiğiniz zaman ek seçenekler desteklenir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XDCMake** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**EkDocumentFile**|İsteğe bağlı **String[]** parametresi.<br /><br /> Birleştirmek için bir veya daha fazla ek *.xdc* dosya belirtir.<br /><br /> Daha fazla bilgi için [XML Document Generator Tool özellik sayfalarındaki](/cpp/build/reference/xml-document-generator-tool-property-pages) **Ek Belge Dosyaları** açıklamasına bakın. Ayrıca *xdcmake.exe*için **/old** ve **/Fs** komut satırı seçeneklerine bakın.|
|**Ek Seçenekler**|İsteğe bağlı **String** parametresi.<br /><br /> Komut satırında belirtilen seçenekler listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **XDCMake** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için, *xdcmake.exe*için [XDCMake referans](/cpp/build/reference/xdcmake-reference), [XML Belge Jeneratör Aracı özellik sayfaları](/cpp/build/reference/xml-document-generator-tool-property-pages)ve komut satırı yardım (**/?**) bakın.|
|**DocumentLibraryBağımlılıklar**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true` Geçerli projede çözümdeki statik kitaplık *(.lib)* projesine bağımlılık varsa, bu kitaplık projesinin *.xdc* dosyaları geçerli proje için *.xml* dosya çıktısı eklenmiştir.<br /><br /> Daha fazla bilgi için [XML Belge Oluşturma Aracı özellik sayfalarındabelge](/cpp/build/reference/xml-document-generator-tool-property-pages) **kitaplığı bağımlılıkları** açıklamasına bakın.|
|**Outputfile**|İsteğe bağlı **String** parametresi.<br /><br /> Varsayılan çıktı dosya adını geçersiz kılar. Varsayılan ad, işlenen ilk *.xdc* dosyasının adından türetilmiştir.<br /><br /> Daha fazla bilgi için, **/out:\<** [XDCMake başvurusunda](/cpp/build/reference/xdcmake-reference)dosya adı>seçeneğine bakın. Ayrıca *xdcmake.exe*için **/old** ve **/Fo** komut satırı seçeneklerine bakın.|
|**Projeadı**|İsteğe bağlı **String** parametresi.<br /><br /> Geçerli projenin adı.|
|**SlashOld**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true`, ek *xdcmake.exe* seçenekleri sağlar.<br /><br /> Daha fazla bilgi için *xdcmake.exe*için **/old** command-line seçeneğine bakın.|
|**Kaynak**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild kaynak dosya öğesi tanımlar.|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için [XDCMake başvurusundaki](/cpp/build/reference/xdcmake-reference) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **String** parametresi.<br /><br /> İzleyici günlüğüiçin dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
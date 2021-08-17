---
title: XDCMake Görev | Microsoft Docs
description: XML belge MSBuild dosyalarını bir xdcmake.exe dosyasıyla bir alan haline dönüştüren XML Belgeleri araç xdcmake.exe XDCMake görevini nasıl .xml öğrenin.
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
ms.openlocfilehash: b5821f567ae06717665f055f23ec19348855d6da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108154"
---
# <a name="xdcmake-task"></a>XDCMake görevi

XML belge açıklaması (*.xdc*)*dosyalarını* birxdcmake.exedosyası haline dönüştüren XML Belgeleri *aracını* (.xmlsarmalar.

 C++ kaynak kodunda belge açıklamalarını sağlarken ve [/doc](/cpp/build/reference/doc-process-documentation-comments-c-cpp) derleyici seçeneğini kullanarak derleseniz bir *.xdc* dosyası oluşturulur. Daha fazla bilgi için bkz. [XDCMake başvurusu,](/cpp/build/reference/xdcmake-reference) [XML Belge](/cpp/build/reference/xml-document-generator-tool-property-pages)Oluşturucu Aracı özellik sayfaları ve komut satırı yardım seçeneği (**/?**) *xdcmake.exe.*

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, *xdcmake.exe* aracı birkaç komut satırı seçeneklerini destekler. /old komut satırı seçeneğini **belirttiğinizde ek** seçenekler de kullanılabilir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XDCMake** görevinin parametreleri açık almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalDocumentFile**|İsteğe **bağlı String[]** parametresi.<br /><br /> Birleştirilecek bir veya daha fazla *ek .xdc* dosyası belirtir.<br /><br /> Daha fazla bilgi için XML **Belge Oluşturucu Aracı özellik** sayfalarındaki Ek Belge Dosyaları [açıklamasına bakın.](/cpp/build/reference/xml-document-generator-tool-property-pages) Ayrıca, komutu **için /old** ve **/Fs** komut satırı *seçeneklerinexdcmake.exe.*|
|**AdditionalOptions**|İsteğe **bağlı Dize** parametresi.<br /><br /> Komut satırda belirtilen seçeneklerin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir **XDCMake** görev parametresi tarafından temsil etmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bkz. [XDCMake başvurusu,](/cpp/build/reference/xdcmake-reference) [XML Belge](/cpp/build/reference/xml-document-generator-tool-property-pages)Oluşturucu Aracı özellik sayfaları ve komut satırı yardımı (**/?**) *xdcmake.exe.*|
|**DocumentLibraryDependencies**|İsteğe **bağlı Boole parametresi.**<br /><br /> ve geçerli projenin çözümde bir statik kitaplık ( .lib ) projesine bağımlılığı varsa, bu kitaplık `true` *projesinin .xdc* dosyaları geçerli projenin *.xml* dosyası çıkışınadahil edilir.<br /><br /> Daha fazla bilgi için XML **Belge Oluşturucu Aracı özellik sayfalarındaki** Belge Kitaplığı [Bağımlılıkları açıklamasına bakın.](/cpp/build/reference/xml-document-generator-tool-property-pages)|
|**Outputfile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılar. Varsayılan ad, işlenen ilk *.xdc dosyasının adı* türetildi.<br /><br /> Daha fazla bilgi için [XDCMake](/cpp/build/reference/xdcmake-reference)başvurusunda **/out: \<filename>** seçeneğine bakın. Ayrıca, komutu **için /old** **ve /Fo** komut satırı *seçeneklerinexdcmake.exe.*|
|**Projeadı**|İsteğe **bağlı Dize** parametresi.<br /><br /> Geçerli projenin adı.|
|**SlashOld**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` ek xdcmake.exesağlar.<br /><br /> Daha fazla bilgi için , için **/old** komut satırı *seçeneğinexdcmake.exe.*|
|**Kaynaklar**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilebilir MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.|
|**SuppressStartupBanner**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **XDCMake başvurusunda /nologo** [seçeneğine bakın.](/cpp/build/reference/xdcmake-reference)|
|**TrackerLogDirectory**|İsteğe **bağlı Dize** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
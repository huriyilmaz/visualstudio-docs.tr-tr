---
title: FXC görevi | Microsoft Docs
description: MSBuild FXC görevinin derleme işlemindeki HLSL gölgelendirici derleyicileri için kullandığı parametreler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: b200fde9e5bc07f654ae2bf11cd8a752efbfe123
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436697"
---
# <a name="fxc-task"></a>FXC görevi

Yapı sürecinde HLSL gölgelendirici derleyicileri kullanın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **fxc** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazlaysa noktalı virgülle ayırın.<br/><br/>`/I[path]` komutunu kullanın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.|
|**Allresourcesbağlanmadı**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici, bir gölgelendiricinin başvurabileceğinizden tüm kaynakların bağlandığını ve gölgelendirici yürütme süresi boyunca iyi durumda olduğunu varsayacaktır. Gölgelendirici modeli 5,1 ve üzeri için kullanılabilir.<br/><br/>`/all_resources_bound` komutunu kullanın.|
|**Lerçıktıyı birleştirin**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme dili çıkış dosyasının içeriğini belirtir.<br/><br/>`/Fc, /Fx` komutunu kullanın.<br/><br/>**NoList**<br/>**Assemblycode**, kullanın `Fc` .<br/>**Assemblycodeandhex**, kullanın `Fx` .|
|**Lerçıktıdosyası**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme kodu liste dosyası için dosya adını belirtir.|
|**CompileD2DCustomEffect**|İsteğe bağlı **bool** parametresi.<br/><br/>Piksel gölgelendiricileri içeren bir Direct2D özel efekti derleyin. Köşe veya işlem özel efekti için kullanmayın.|
|**Tüketimeexportfile**|İsteğe bağlı **dize** parametresi.|
|**Disableiyileştirmeleri**|İsteğe bağlı **bool** parametresi.<br/><br/>İyileştirmeleri devre dışı bırakın.<br/><br/>`/Od``/Gfp`çıktının ile aynı olamaz `/Od /Gfp` .|
|**EnableDebuggingInformation**|İsteğe bağlı **bool** parametresi.<br/><br/>Hata ayıklama bilgilerini etkinleştirin.|
|**EnableUnboundedDescriptorTables**|İsteğe bağlı **bool** parametresi.<br/><br/>Bir gölgelendiriciye, sınırlandırılmamış aralığa sahip bir kaynak dizisinin bildirimini içerdiğini bildirin. Gölgelendirici modeli 5,1 ve üzeri için kullanılabilir.<br/><br/>`/enable_unbounded_descriptor_tables` komutunu kullanın.|
|**EntryPointName**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici için giriş noktasının adını belirtir.<br/><br/>`/E[name]` komutunu kullanın.|
|**GenerateExportFile**|İsteğe bağlı **dize** parametresi.|
|**GenerateExportShaderProfile**|İsteğe bağlı **dize** parametresi.|
|**HeaderFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne kodu içeren üstbilgi dosyası için bir ad belirtir.<br/><br/>`/Fh [name]` komutunu kullanın.|
|**ObjectFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne dosyası için bir ad belirtir.<br/><br/>`/Fo [name]` komutunu kullanın.|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Kaynak dosyanız için ön işleme sembollerini tanımlar.|
|**SetRootSignature**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici bytecode 'a kök imzası iliştirin. Gölgelendirici modeli 5,0 ve üzeri için kullanılabilir.<br/><br/>`/setrootsignature` komutunu kullanın.|
|**ShaderModel**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici modelini belirtir. Bazı gölgelendirici türleri yalnızca son gölgelendirici modelleriyle kullanılabilir.<br/><br/>`/T [type]_[model]` komutunu kullanın.|
|**ShaderType**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici türünü belirtir.<br/><br/>`/T [type]_[model]` komutunu kullanın.<br/><br/>**Efekt**, kullanın `fx` .<br/>**Köşe**, kullanın `vs` .<br/>**Piksel**, kullanın `ps` .<br/>**Geometri**, kullanın `gs` .<br/>**Hull**, kullanın `hs` .<br/>**Etki alanı**, kullanın `ds` .<br/>**İşlem**, kullanın `cs` .<br/>**Kitaplığı**kullanın `lib` .<br/>**Rootsignature**, kök imza nesnesi oluştur.|
|**Kaynak**|Gerekli **ıtaskitem** parametresi.|
|**SuppressStartupBanner**|İsteğe bağlı **bool** parametresi.<br/><br/>Başlangıç başlığının ve bilgi iletisinin görüntülenmesini önler.<br/><br/>`/nologo` komutunu kullanın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|
|**TreatWarningAsError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak değerlendirir.<br/><br/>Yeni bir proje için tüm derlemelerde kullanılması en iyi yöntem olabilir `/WX` ; Tüm uyarıların çözümlenmesi, en az olası bir hata bulma kod kusurlarını güvence altına alacak.|
|**VariableName**|İsteğe bağlı **dize** parametresi.<br/><br/>Üstbilgi dosyasındaki değişken adı için bir ad belirtir.<br/><br/>`/Vn [name]` komutunu kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
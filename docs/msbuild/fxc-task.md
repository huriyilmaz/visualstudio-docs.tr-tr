---
title: FXC Görev | Microsoft Docs
description: FXC görevinin derleme MSBuild HLSL gölgelendirici derleyicileri için kullandığı parametreler hakkında bilgi öğrenin.
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
ms.openlocfilehash: 7f98bc7790f3d5e8ae4e28e83428ce350e2e7430a2e6327f3a2a559e86e37370
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427853"
---
# <a name="fxc-task"></a>FXC görevi

Derleme sürecinde HLSL gölgelendirici derleyicilerini kullanın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda FXC görevinin **parametreleri açık** almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe **bağlı string[]** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazla ise noktalı virgülle ayır.<br/><br/>`/I[path]` komutunu kullanın.|
|**AdditionalOptions**|İsteğe **bağlı dize** parametresi.|
|**AllResourcesBound**|İsteğe **bağlı bool** parametresi.<br/><br/>Derleyici, bir gölgelendiricinin başvura tüm kaynakların bağlı olduğunu ve gölgelendirici yürütmesi süresince iyi durumda olduğunu varsayacak. Gölgelendirici Modeli 5.1 ve üzeri için kullanılabilir.<br/><br/>`/all_resources_bound` komutunu kullanın.|
|**AssemblerOutput**|İsteğe **bağlı dize** parametresi.<br/><br/>Derleme dili çıkış dosyasının içeriğini belirtir.<br/><br/>`/Fc, /Fx` komutunu kullanın.<br/><br/>**NoListing**<br/>**AssemblyCode**, `Fc` kullanın.<br/>**AssemblyCodeAndHex**, `Fx` kullanın.|
|**AssemblerOutputFile**|İsteğe **bağlı dize** parametresi.<br/><br/>Derleme kodu listeleme dosyası için dosya adını belirtir.|
|**CompileD2DCustomEffect**|İsteğe **bağlı bool** parametresi.<br/><br/>Piksel gölgelendiricileri içeren bir Direct2D özel etkisi derle. Köşe veya işlem özel etkisi için kullanmayın.|
|**ConsumeExportFile**|İsteğe **bağlı dize** parametresi.|
|**DisableOptimizations**|İsteğe **bağlı bool** parametresi.<br/><br/>İyileştirmeleri devre dışı bırakma.<br/><br/>`/Od` , `/Gfp` çıkışının ile aynı olmadığını `/Od /Gfp` belirtir.|
|**EnableDebuggingInformation**|İsteğe **bağlı bool** parametresi.<br/><br/>Hata ayıklama bilgilerini etkinleştirin.|
|**EnableUnboundedDescriptorTables**|İsteğe **bağlı bool** parametresi.<br/><br/>Derleyiciye bir gölgelendiricinin sınırsız aralık içeren bir kaynak dizisi bildirimi içere içere olduğunu bildirin. Gölgelendirici Modeli 5.1 ve üzeri için kullanılabilir.<br/><br/>`/enable_unbounded_descriptor_tables` komutunu kullanın.|
|**EntryPointName**|İsteğe **bağlı dize** parametresi.<br/><br/>Gölgelendirici için giriş noktasının adını belirtir.<br/><br/>`/E[name]` komutunu kullanın.|
|**GenerateExportFile**|İsteğe **bağlı dize** parametresi.|
|**GenerateExportShaderProfile**|İsteğe **bağlı dize** parametresi.|
|**HeaderFileOutput**|İsteğe **bağlı dize** parametresi.<br/><br/>Nesne kodu içeren üst bilgi dosyası için bir ad belirtir.<br/><br/>`/Fh [name]` komutunu kullanın.|
|**ObjectFileOutput**|İsteğe **bağlı dize** parametresi.<br/><br/>Nesne dosyası için bir ad belirtir.<br/><br/>`/Fo [name]` komutunu kullanın.|
|**ÖnişlemciDefinitions**|İsteğe **bağlı string[]** parametresi.<br/><br/>Kaynak dosyanız için ön işleme sembollerini tanımlar.|
|**SetRootSignature**|İsteğe **bağlı dize** parametresi.<br/><br/>Gölgelendirici bytecode'a kök imza ekleme. Gölgelendirici Modeli 5.0 ve üzeri için kullanılabilir.<br/><br/>`/setrootsignature` komutunu kullanın.|
|**ShaderModel**|İsteğe **bağlı dize** parametresi.<br/><br/>Gölgelendirici modelini belirtir. Bazı gölgelendirici türleri yalnızca son gölgelendirici modelleriyle kullanılabilir.<br/><br/>`/T [type]_[model]` komutunu kullanın.|
|**ShaderType**|İsteğe **bağlı dize** parametresi.<br/><br/>Gölgelendiricinin türünü belirtir.<br/><br/>`/T [type]_[model]` komutunu kullanın.<br/><br/>**Etkisi,** `fx` kullanın.<br/>**Köşe,** `vs` kullanın.<br/>**Piksel,** `ps` kullanın.<br/>**Geometri,** `gs` kullanın.<br/>**Gövde,** `hs` kullanın.<br/>**Etki** alanı, `ds` kullanın.<br/>**İşlem,** `cs` kullanın.<br/>**Kitaplığı,** `lib` kullanın.<br/>**RootSignature**, Kök İmza Nesnesi oluşturur.|
|**Kaynak**|Gerekli **ITaskItem** parametresi.|
|**SuppressStartupBanner**|İsteğe **bağlı bool** parametresi.<br/><br/>Başlangıç başlığı ve bilgi iletisi görüntülenmez.<br/><br/>`/nologo` komutunu kullanın.|
|**TrackerLogDirectory**|İsteğe **bağlı dize** parametresi.|
|**TreatWarningAsError**|İsteğe **bağlı bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak davranır.<br/><br/>Yeni bir proje için tüm derlemelerde kullanılması en iyi yöntem olabilir `/WX` ; Tüm uyarıların çözümlenmesi, en az olası bir hata bulma kod kusurlarını güvence altına alacak.|
|**VariableName**|İsteğe bağlı **dize** parametresi.<br/><br/>Üstbilgi dosyasındaki değişken adı için bir ad belirtir.<br/><br/>`/Vn [name]` komutunu kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
---
title: FXC görevi | Microsoft Docs
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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 766a3dc35d72e21fc0aca9436ebff25dc3193a2e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747332"
---
# <a name="fxc-task"></a>FXC görevi

Yapı sürecinde HLSL gölgelendirici derleyicileri kullanın.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda **fxc** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br/><br/>Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazlaysa noktalı virgülle ayırın.<br/><br/>@No__t_0 kullanın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.|
|**Allresourcesbağlanmadı**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici, bir gölgelendiricinin başvurabileceğinizden tüm kaynakların bağlandığını ve gölgelendirici yürütme süresi boyunca iyi durumda olduğunu varsayacaktır. Gölgelendirici modeli 5,1 ve üzeri için kullanılabilir.<br/><br/>@No__t_0 kullanın.|
|**Lerçıktıyı birleştirin**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme dili çıkış dosyasının içeriğini belirtir.<br/><br/>@No__t_0 kullanın.<br/><br/>**NoList**<br/>**Assemblycode**, `Fc` kullanın.<br/>**Assemblycodeandhex**, `Fx` kullanın.|
|**Lerçıktıdosyası**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme kodu liste dosyası için dosya adını belirtir.|
|**CompileD2DCustomEffect**|İsteğe bağlı **bool** parametresi.<br/><br/>Piksel gölgelendiricileri içeren bir Direct2D özel efekti derleyin. Köşe veya işlem özel efekti için kullanmayın.|
|**Tüketimeexportfile**|İsteğe bağlı **dize** parametresi.|
|**Disableiyileştirmeleri**|İsteğe bağlı **bool** parametresi.<br/><br/>İyileştirmeleri devre dışı bırakın.<br/><br/>`/Od`, çıktı `/Od /Gfp` ile aynı olamaz `/Gfp` anlamına gelir.|
|**EnableDebuggingInformation**|İsteğe bağlı **bool** parametresi.<br/><br/>Hata ayıklama bilgilerini etkinleştirin.|
|**EnableUnboundedDescriptorTables**|İsteğe bağlı **bool** parametresi.<br/><br/>Bir gölgelendiriciye, sınırlandırılmamış aralığa sahip bir kaynak dizisinin bildirimini içerdiğini bildirin. Gölgelendirici modeli 5,1 ve üzeri için kullanılabilir.<br/><br/>@No__t_0 kullanın.|
|**EntryPointName**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici için giriş noktasının adını belirtir.<br/><br/>@No__t_0 kullanın.|
|**GenerateExportFile**|İsteğe bağlı **dize** parametresi.|
|**GenerateExportShaderProfile**|İsteğe bağlı **dize** parametresi.|
|**HeaderFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne kodu içeren üstbilgi dosyası için bir ad belirtir.<br/><br/>@No__t_0 kullanın.|
|**ObjectFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne dosyası için bir ad belirtir.<br/><br/>@No__t_0 kullanın.|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br/><br/>Kaynak dosyanız için ön işleme sembollerini tanımlar.|
|**SetRootSignature**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici bytecode 'a kök imzası iliştirin. Gölgelendirici modeli 5,0 ve üzeri için kullanılabilir.<br/><br/>@No__t_0 kullanın.|
|**ShaderModel**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici modelini belirtir. Bazı gölgelendirici türleri yalnızca son gölgelendirici modelleriyle kullanılabilir.<br/><br/>@No__t_0 kullanın.|
|**ShaderType**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgelendirici türünü belirtir.<br/><br/>@No__t_0 kullanın.<br/><br/>**Efekt**, `fx` kullanın.<br/>**Köşe**, `vs` kullanın.<br/>**Piksel**, `ps` kullanın.<br/>**Geometri**, `gs` kullanın.<br/>**Hull**, `hs` kullanın.<br/>**Etki alanı**`ds` kullanın.<br/>**İşlem**, `cs` kullanın.<br/>**Kitaplığı**`lib` kullanın.<br/>**Rootsignature**, kök imza nesnesi oluştur.|
|**Kaynaktaki**|Gerekli **ıtaskitem** parametresi.|
|**SuppressStartupBanner**|İsteğe bağlı **bool** parametresi.<br/><br/>Başlangıç başlığının ve bilgi iletisinin görüntülenmesini önler.<br/><br/>@No__t_0 kullanın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|
|**TreatWarningAsError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak değerlendirir.<br/><br/>Yeni bir proje için tüm derlemelerde `/WX` kullanılması en iyi yöntem olabilir; Tüm uyarıların çözümlenmesi, en az olası bulma kod kusurlarını güvence altına alacak.|
|**VariableName**|İsteğe bağlı **dize** parametresi.<br/><br/>Üstbilgi dosyasındaki değişken adı için bir ad belirtir.<br/><br/>@No__t_0 kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
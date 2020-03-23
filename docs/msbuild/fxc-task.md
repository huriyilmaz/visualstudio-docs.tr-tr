---
title: FXC Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 67958a1a1ebb2ff382d0896e2fbaec6105c0c785
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279290"
---
# <a name="fxc-task"></a>FXC görevi

Yapı işleminde HLSL shader derleyicilerini kullanın.

## <a name="parameters"></a>Parametreler

Aşağıdaki **tabloda FXC** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**EkIncludeDirectories**|İsteğe bağlı **dize[]** parametresi.<br/><br/>İçle yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazla ise yarı-kolon ile ayrı.<br/><br/>`/I[path]` adresini kullanın.|
|**Ek Seçenekler**|İsteğe bağlı **dize** parametresi.|
|**AllResourcesBound**|İsteğe bağlı **bool** parametresi.<br/><br/>Derleyici, bir gölgeleyicinin başvuruda bulunabileceği tüm kaynakların bağlı olduğunu ve gölgeli yürütme süresince iyi durumda olduğunu varsayacaktır. Shader Model 5.1 ve üzeri için kullanılabilir.<br/><br/>`/all_resources_bound` adresini kullanın.|
|**AssemblerÇıktı**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme dili çıktı dosyasının içeriğini belirtir.<br/><br/>`/Fc, /Fx` adresini kullanın.<br/><br/>**NoListing**<br/>**AssemblyCode**, `Fc`kullanın.<br/>**AssemblyCodeAndHex**, `Fx`kullanın .|
|**AssemblerOutputFile**|İsteğe bağlı **dize** parametresi.<br/><br/>Derleme kodu listeleme dosyası için dosya adını belirtir.|
|**CompileD2DCustomEffect**|İsteğe bağlı **bool** parametresi.<br/><br/>Piksel gölgeleyiciler içeren Direct2D özel efekti derle. Bir vertex veya işlem özel efekt için kullanmayın.|
|**ConsumeExportFile**|İsteğe bağlı **dize** parametresi.|
|**Devre Dışı BırakmaOptimizasyonları**|İsteğe bağlı **bool** parametresi.<br/><br/>Optimizasyonları devre dışı bırakmak.<br/><br/>`/Od`çıktı `/Gfp` ile `/Od /Gfp`aynı olmayabilir ama ima eder.|
|**EtkinleştirMeHata İşlemi**|İsteğe bağlı **bool** parametresi.<br/><br/>Hata ayıklama bilgilerini etkinleştirin.|
|**EnableUnboundedDescriptorTablolar**|İsteğe bağlı **bool** parametresi.<br/><br/>Bir gölgeli sınırsız aralığı olan bir kaynak dizisinin bildirimi içerebilir derleyici bildirin. Shader Model 5.1 ve üzeri için kullanılabilir.<br/><br/>`/enable_unbounded_descriptor_tables` adresini kullanın.|
|**EntryPointName**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgeli için giriş noktasının adını belirtir.<br/><br/>`/E[name]` adresini kullanın.|
|**OluşturmaExportFile**|İsteğe bağlı **dize** parametresi.|
|**OluşturmaExportShaderProfile**|İsteğe bağlı **dize** parametresi.|
|**HeaderFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne kodu içeren üstbilgi dosyası için bir ad belirtir.<br/><br/>`/Fh [name]` adresini kullanın.|
|**ObjectFileOutput**|İsteğe bağlı **dize** parametresi.<br/><br/>Nesne dosyası için bir ad belirtir.<br/><br/>`/Fo [name]` adresini kullanın.|
|**Önİşleme İşlemci Tanımlar**|İsteğe bağlı **dize[]** parametresi.<br/><br/>Kaynak dosyanız için ön işleme sembolleri tanımlar.|
|**SetRootSignature**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgeli bayt koduna kök imzası ekle. Shader Model 5.0 ve üzeri için kullanılabilir.<br/><br/>`/setrootsignature` adresini kullanın.|
|**ShaderModel**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgeli modeli belirtir. Bazı gölgeli türleri yalnızca son gölgeli modellerde kullanılabilir.<br/><br/>`/T [type]_[model]` adresini kullanın.|
|**ShaderType**|İsteğe bağlı **dize** parametresi.<br/><br/>Gölgeli türünü belirtir.<br/><br/>`/T [type]_[model]` adresini kullanın.<br/><br/>**Etkisi**, `fx`kullanın .<br/>**Vertex**, `vs`kullanın .<br/>**Piksel**, `ps`kullanın .<br/>**Geometri**, `gs`kullanın .<br/>**Gövde**, `hs`kullanın .<br/>**Etki**alanı `ds`, kullanın .<br/>**İşlem ,** kullanın `cs`.<br/>**Kütüphane**, `lib`kullanın .<br/>**RootSignature**, Kök İmza Nesnesi oluşturun.|
|**Kaynak**|Gerekli **ITaskItem** parametresi.|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı **bool** parametresi.<br/><br/>Başlangıç afişinin ve bilgi iletisinin ekranını bastırır.<br/><br/>`/nologo` adresini kullanın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.|
|**TreatWarningasError**|İsteğe bağlı **bool** parametresi.<br/><br/>Tüm derleyici uyarılarını hata olarak ele akurum.<br/><br/>Yeni bir proje için, tüm `/WX` derlemelerde kullanmak en iyisi olabilir; tüm uyarıların çözülmesi, bulunması mümkün olan en az kod hatasını sağlayacaktır.|
|**VariableName**|İsteğe bağlı **dize** parametresi.<br/><br/>Üstbilgi dosyasındaki değişken adının adını belirtir.<br/><br/>`/Vn [name]` adresini kullanın.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
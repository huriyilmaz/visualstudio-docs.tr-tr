---
title: MT Görev | Microsoft Docs
description: MSBuild MT görevinin Microsoft Bildirim Aracı'nı sarmalar ve komut satırı seçenekleri hakkında bilgi mt.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6463108b2cad5c015752e48c8c3616300479efb176288c2784e49a43901b839c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397325"
---
# <a name="mt-task"></a>MT görevi

Microsoft Bildirim Aracı'nı sarmalar ve *mt.exe.* Daha fazla bilgi için [bkz.Mt.exe. ](/windows/desktop/SbsCs/mt-exe)

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda MT görevinin parametreleri **açık** almaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelen bir seçenektir.

> [!NOTE]
> Bu *mt.exe,* komut satırı seçenekleri için ön ek olarak kısa çizgi ( **-** ) kullanır, ancak bu konuda eğik çizgi ( ) lanmıştır. **/** Her iki ön ek de kabul edilebilir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalManifestFiles**|İsteğe **bağlı String[]** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyalarının adını belirtir.<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**AdditionalOptions**|İsteğe **bağlı Dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir MT görev parametresiyle temsil etmeyen komut satırı seçeneklerini belirtmek için **bu** parametreyi kullanın.<br /><br /> Daha fazla bilgi için [bkz.Mt.exe. ](/windows/desktop/SbsCs/mt-exe)|
|**Assemblyıdentity**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bildirimin **assemblyIdentity öğesinin öznitelik** değerlerini belirtir. Virgülle ayrılmış bir liste belirtin; burada ilk bileşen özniteliğin değeridir ve ardından formu olan bir veya daha fazla ad/değer çifti ( `name` *\<attribute name> =*<attribute_value>).<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**ComponentFileName**|İsteğe **bağlı Dize** parametresi.<br /><br /> *.rgs* veya *.tlb* dosyalarından derlemek istediğiniz dynamic-link kitaplığının adını belirtir. **RegistrarScriptFile** veya **TypeLibraryFile** MT görev parametrelerini belirtirsiniz, bu parametre gereklidir.<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**DependencyInformationFile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bildirim aracı için derleme bağımlılık bilgilerini izlemek Visual Studio tarafından kullanılan bağımlılık bilgileri dosyasını belirtir.|
|**EmbedManifest**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` bildirim dosyasını derlemeye katıştırır. ise, `false` tek başına bildirim dosyası olarak oluşturur.|
|**EnableDPIAwareness**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` uygulamayı DPI'yi fark etti olarak işaretleyen bildirim bilgilerine ekler. DPI'yi farkeden bir uygulama yazmak, kullanıcı arabiriminin çok çeşitli yüksek DPI görüntü ayarlarında tutarlı bir şekilde iyi bir görünüme sahip olmasını sağlar.<br /><br /> Daha fazla bilgi için bkz. [Yüksek DPI.](/windows/desktop/win7devguide/high-dpi)|
|**GenerateCatalogFiles**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise `true` katalog tanımı (*.cdf*) dosyaları oluşturur.<br /><br /> Daha fazla bilgi için, içinde **/makecdfs** seçeneğine [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**GenerateCategoryTags**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` kategori etiketlerinin oluşturularak oluşturulur. Bu parametre `true` ise, **ManifestFromManagedAssemblyMT** görev parametresi de belirtilmelidir.<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**InputResourceManifests**|İsteğe **bağlı Dize** parametresi.<br /><br /> Belirtilen tanımlayıcıya sahip olan RT_MANIFEST kaynağından bildirimi girdi. Formun bir kaynağını belirtin, \<file> [;[ #] \<resource_id> ], burada isteğe \<resource_id> bağlı parametresi negatif olmayan, 16 bit bir sayıdır.<br /><br /> `resource_id`belirtilmezse, varsayılan CREATEPROCESS_MANIFEST_RESOURCE (1) kullanılır.<br /><br /> Daha fazla bilgi için, içinde **/inputresource** seçeneğine [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**ManifestFromManagedAssembly**|İsteğe **bağlı Dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim üretir.<br /><br /> Daha fazla bilgi için, içinde **/managedassemblyname** seçeneğine [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**ManifestToIgnore**|İsteğe **bağlı Dize** parametresi.<br /><br /> (Kullanılmadı.)|
|**OutputManifestFile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Çıkış bildiriminin adını belirtir. Bu parametre atlanırsa ve yalnızca bir bildirim çalıştıriliyorsa, bu bildirim yerinde değiştirilir.<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**OutputResourceManifests**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bildirimi belirtilen tanımlayıcıya sahip bir RT_MANIFEST kaynağına çıkış olarak verir. Kaynak şu şekildedir: \<file> [;[ #] \<resource_id> ], burada isteğe \<resource_id> bağlı parametresi negatif olmayan, 16 bit bir sayıdır.<br /><br /> `resource_id`belirtilmezse, varsayılan CREATEPROCESS_MANIFEST_RESOURCE (1) kullanılır.<br /><br /> Daha fazla bilgi için **bkz.** Mt.exe [.](/windows/desktop/SbsCs/mt-exe)|
|**RegistrarScriptFile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Kayıtsız COM bildirim desteği için kullanmak üzere kayıt şirketi betiği (*.rgs*) dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için bkz. [](/windows/desktop/SbsCs/mt-exe) **Mt.exe.**|
|**DeğiştirmelerDosyası**|İsteğe **bağlı Dize** parametresi.<br /><br /> Kayıt şirketi betiği (*.rgs*) dosyasındaki değiştirilebilir dizelerin değerlerini içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için, içinde **/replacements** [seçeneğineMt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**ResourceOutputFileName**|İsteğe **bağlı Dize** parametresi.<br /><br /> Bildirimi proje çıkışına eklemek için kullanılan çıkış kaynakları dosyasını belirtir.|
|**Kaynaklar**|İsteğe `ITaskItem[]` bağlı parametre.<br /><br /> Boşluklarla ayrılmış bildirim kaynak dosyalarının listesini belirtir.<br /><br /> Daha fazla bilgi için **bkz.** [Mt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**SuppressDependencyElement**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` bağımlılık öğeleri olmadan bir bildirim üretir. Bu parametre `true` ise, **ManifestFromManagedAssemblyMT görev parametresini de** belirtin.<br /><br /> Daha fazla bilgi için, içinde **/nodependency** [seçeneğineMt.exe.](/windows/desktop/SbsCs/mt-exe)|
|**SuppressStartupBanner**|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.|
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığı (*. tlb*) dosyasının adını belirtir. Bu parametreyi belirtirseniz, **ComponentFileNameMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/tlb** seçeneğine bakın.|
|**Updatefilekarmaları**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, **UpdateFileHashesSearchPathMT** görev parametresi tarafından belirtilen yoldaki dosyaların karma değerini hesaplar ve ardından Hesaplanan değeri kullanarak bildirimin **Dosya** öğesinin **karma** özniteliğinin değerini güncelleştirir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/hashupdate** seçeneğine bakın. Ayrıca bkz. bu tablodaki **UpdateFileHashesSearchPath** parametresi.|
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametre.<br /><br /> Dosya karmaları güncelleştirilirken kullanılacak arama yolunu belirtir. **UpdateFileHashesMT** görev parametresiyle bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bu tablodaki **Updatefilekarmaları** parametresine bakın.|
|**VerboseOutput**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için, [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)

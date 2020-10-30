---
title: MT görevi | Microsoft Docs
description: Microsoft bildirim aracı mt.exe sarmalayan MSBuild MT görevinin parametreleri ve komut satırı seçenekleri hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5ce7e602c3f95766fdade297c2ee235cebba24c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048992"
---
# <a name="mt-task"></a>MT görevi

Microsoft Bildirim Aracı ' nı sarmalayan *mt.exe* . Daha fazla bilgi için bkz. [Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, **MT** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

> [!NOTE]
> *mt.exe* belgeleri **-** komut satırı seçeneklerinin ön eki olarak bir tire () kullanır, ancak bu konu eğik çizgi ( **/** ) kullanır. Her iki önek de kabul edilebilir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalManifestFiles**|İsteğe bağlı **dize []** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/MANIFEST** seçeneğine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **MT** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bkz. [Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimin **assemblyIdentity** öğesinin öznitelik değerlerini belirtir. İlk bileşen özniteliğin değeri, `name` ardından, *\<attribute name> =<attribute_value>* olan bir veya daha fazla ad/değer çifti olduğunda, virgülle ayrılmış bir liste belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/Identity** seçeneğine bakın.|
|**ComponentFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> *. Rgs* veya *. tlb* dosyalarından oluşturmayı düşündüğünüz dinamik bağlantı kitaplığının adını belirtir. **RegistrarScriptFile** veya **TypeLibraryFile** MT görev parametrelerini belirtirseniz bu parametre gereklidir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/DLL** seçeneğine bakın.|
|**Dependencyınformationfile**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirim aracına yönelik derleme bağımlılığı bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgi dosyasını belirtir.|
|**EmbedManifest**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bildirim dosyasını derlemeye gömer. İse `false` , tek başına bildirim dosyası olarak oluşturulur.|
|**Enabledpitanıma**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , uygulamayı DPI kullanan olarak işaretleyen bildirim bilgilerine ekler. DPı kullanan bir uygulama yazmak, bir kullanıcı arabiriminin çok çeşitli yüksek DPı ekran ayarları boyunca sürekli olarak iyi görünmesini sağlar.<br /><br /> Daha fazla bilgi için bkz. [yüksek DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , Katalog tanımı ( *. cdf* ) dosyaları oluşturur.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/makecdfs** seçeneğine bakın.|
|**GenerateCategoryTags**|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` Kategori etiketlerinin oluşturulmasına neden olur. Bu parametre ise `true` , **ManifestFromManagedAssemblyMT** görev parametresinin de belirtilmesi gerekir.<br /><br /> Daha fazla bilgi için, [Mt.exe](/windows/desktop/SbsCs/mt-exe)için **/category** seçeneğine bakın.|
|**Inputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynaktan bildirim girin. \<file>[; [ #] \<resource_id> ], burada isteğe bağlı \<resource_id> parametre negatif olmayan, 16 bit bir sayıdır.<br /><br /> Hayır `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/ınputresource** seçeneğine bakın.|
|**ManifestFromManagedAssembly**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/managedassemblyname** seçeneğine bakın.|
|**Manifesttoıgnore**|İsteğe bağlı **dize** parametresi.<br /><br /> (Kullanılmıyor.)|
|**OutputManifestFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış bildiriminin adını belirtir. Bu parametre atlanırsa ve üzerinde yalnızca bir bildirim işletilebilir, bu bildirim yerinde değiştirilir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/Out** seçeneğine bakın.|
|**Outputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynağa çıkış. Kaynak, \<file> [; [ #] \<resource_id> ], burada isteğe bağlı \<resource_id> parametre negatif olmayan, 16 bit bir sayıdır.<br /><br /> Hayır `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/outputresource** seçeneğine bakın.|
|**RegistrarScriptFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kayıtsız COM bildirim desteği için kullanılacak kaydedici betiği ( *. rgs* ) dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)' de **/r GS** seçeneğine bakın.|
|**ReplacementsFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betiği ( *. rgs* ) dosyasındaki değiştirilebilen dizelerin değerlerini içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/değiştirmeleri** seçeneğine bakın.|
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi proje çıkışına katıştırmak için kullanılan çıkış kaynakları dosyasını belirtir.|
|**Ğına**|İsteğe bağlı `ITaskItem[]` parametre.<br /><br /> Boşluklarla ayrılmış bildirim kaynak dosyalarının bir listesini belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/MANIFEST** seçeneğine bakın.|
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bağımlılık öğeleri olmayan bir bildirim oluşturur. Bu parametre ise `true` , **ManifestFromManagedAssemblyMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/nodependency** seçeneğine bakın.|
|**SuppressStartupBanner**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.|
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığı ( *. tlb* ) dosyasının adını belirtir. Bu parametreyi belirtirseniz, **ComponentFileNameMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/tlb** seçeneğine bakın.|
|**Updatefilekarmaları**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, **UpdateFileHashesSearchPathMT** görev parametresi tarafından belirtilen yoldaki dosyaların karma değerini hesaplar ve ardından Hesaplanan değeri kullanarak bildirimin **Dosya** öğesinin **karma** özniteliğinin değerini güncelleştirir.<br /><br /> Daha fazla bilgi için [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/hashupdate** seçeneğine bakın. Ayrıca bkz. bu tablodaki **UpdateFileHashesSearchPath** parametresi.|
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametre.<br /><br /> Dosya karmaları güncelleştirilirken kullanılacak arama yolunu belirtir. **UpdateFileHashesMT** görev parametresiyle bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bu tablodaki **Updatefilekarmaları** parametresine bakın.|
|**VerboseOutput**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için, [Mt.exe](/windows/desktop/SbsCs/mt-exe)içindeki **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)

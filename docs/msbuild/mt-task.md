---
title: MT görevi | Microsoft Docs
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
ms.openlocfilehash: 5fe0ce106fc471431d3aac088eb3f45cfb28c564
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633063"
---
# <a name="mt-task"></a>MT görevi

Microsoft bildirim aracı olan *mt. exe*' yi kaydırır. Daha fazla bilgi için bkz. [mt. exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, **MT** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

> [!NOTE]
> *Mt. exe* belgeleri komut satırı seçeneklerinin ön eki olarak bir tire işareti ( **-** ) kullanır, ancak bu konu eğik çizgi ( **/** ) kullanır. Her iki önek de kabul edilebilir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalManifestFiles**|İsteğe bağlı **dize []** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/MANIFEST** seçeneğine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin,/\<Seçenek1 >/\<Seçenek2 >/\<Seçenek # >. Başka bir **MT** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bkz. [mt. exe](/windows/desktop/SbsCs/mt-exe).|
|**AssemblyIdentity**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimin **assemblyIdentity** öğesinin öznitelik değerlerini belirtir. İlk bileşenin `name` özniteliğin değeri olduğu, ardından bir veya daha fazla ad/değer çifti olan, *\<öznitelik adı > = < attribute_value >* olan virgülle ayrılmış bir liste belirtin.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/Identity** seçeneğine bakın.|
|**ComponentFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> *. Rgs* veya *. tlb* dosyalarından oluşturmayı düşündüğünüz dinamik bağlantı kitaplığının adını belirtir. **RegistrarScriptFile** veya **TypeLibraryFile** MT görev parametrelerini belirtirseniz bu parametre gereklidir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/DLL** seçeneğine bakın.|
|**Dependencyınformationfile**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirim aracına yönelik derleme bağımlılığı bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgi dosyasını belirtir.|
|**EmbedManifest**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, bildirim dosyasını derlemeye gömer. `false`, tek başına bildirim dosyası olarak oluşturulur.|
|**Enabledpitanıma**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, uygulamayı DPı kullanan olarak işaretleyen bildirim bilgilerine ekler. DPı kullanan bir uygulama yazmak, bir kullanıcı arabiriminin çok çeşitli yüksek DPı ekran ayarları boyunca sürekli olarak iyi görünmesini sağlar.<br /><br /> Daha fazla bilgi için bkz. [yüksek DPI](/windows/desktop/win7devguide/high-dpi).|
|**GenerateCatalogFiles**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, Katalog tanımı ( *. cdf*) dosyaları oluşturur.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/makecdfs** seçeneğine bakın.|
|**GenerateCategoryTags**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, kategori etiketlerinin oluşturulmasına neden olur. Bu parametre `true`, **ManifestFromManagedAssemblyMT** görev parametresinin de belirtilmesi gerekir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/category** seçeneğine bakın.|
|**Inputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynaktan bildirim girin. \<Dosya > [; [ #] resource_id >]\<, burada isteğe bağlı \<resource_id > parametresi negatif olmayan, 16 bit bir sayı.<br /><br /> `resource_id` belirtilmemişse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/ınputresource** seçeneğine bakın.|
|**ManifestFromManagedAssembly**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/managedassemblyname** seçeneğine bakın.|
|**Manifesttoıgnore**|İsteğe bağlı **dize** parametresi.<br /><br /> (Kullanılmıyor.)|
|**OutputManifestFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış bildiriminin adını belirtir. Bu parametre atlanırsa ve üzerinde yalnızca bir bildirim işletilebilir, bu bildirim yerinde değiştirilir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/Out** seçeneğine bakın.|
|**Outputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynağa çıkış. Kaynak, \<Dosya > [; [ #] resource_id >]\<, burada isteğe bağlı \<resource_id > parametresi negatif olmayan, 16 bit bir sayı.<br /><br /> `resource_id` belirtilmemişse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/outputresource** seçeneğine bakın.|
|**RegistrarScriptFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kayıtsız COM bildirim desteği için kullanılacak kaydedici betiği ( *. rgs*) dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/r GS** seçeneğine bakın.|
|**ReplacementsFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betiği ( *. rgs*) dosyasındaki değiştirilebilen dizelerin değerlerini içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/değiştirmeleri** seçeneğine bakın.|
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi proje çıkışına katıştırmak için kullanılan çıkış kaynakları dosyasını belirtir.|
|**Ğına**|İsteğe bağlı `ITaskItem[]` parametresi.<br /><br /> Boşluklarla ayrılmış bildirim kaynak dosyalarının bir listesini belirtir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/MANIFEST** seçeneğine bakın.|
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, bağımlılık öğeleri olmayan bir bildirim oluşturur. Bu parametre `true`ise, **ManifestFromManagedAssemblyMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/nodependency** seçeneğine bakın.|
|**SuppressStartupBanner**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı `String` parametresi.<br /><br /> Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.|
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığı ( *. tlb*) dosyasının adını belirtir. Bu parametreyi belirtirseniz, **ComponentFileNameMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/tlb** seçeneğine bakın.|
|**Updatefilekarmaları**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, **UpdateFileHashesSearchPathMT** görev parametresi tarafından belirtilen yoldaki dosyaların karma değerini hesaplar ve ardından Hesaplanan değeri kullanarak bildirimin **Dosya** öğesinin **karma** özniteliğinin değerini güncelleştirir.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/hashupdate** seçeneğine bakın. Ayrıca bkz. bu tablodaki **UpdateFileHashesSearchPath** parametresi.|
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametresi.<br /><br /> Dosya karmaları güncelleştirilirken kullanılacak arama yolunu belirtir. **UpdateFileHashesMT** görev parametresiyle bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bu tablodaki **Updatefilekarmaları** parametresine bakın.|
|**VerboseOutput**|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için, [mt. exe](/windows/desktop/SbsCs/mt-exe)' de **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)

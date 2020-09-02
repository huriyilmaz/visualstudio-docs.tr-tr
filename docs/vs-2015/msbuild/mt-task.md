---
title: MT görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBUILD (Visual C++), MT task
- MT task (MSBuild (Visual C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d705bff368e813bdd2c7fe2b60ba9ada8f679bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845964"
---
# <a name="mt-task"></a>MT Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Bildirim Aracı ' nı sarmalayan mt.exe. Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" başlığına bakın.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, **MT** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.  
  
> [!NOTE]
> mt.exe belgeleri **-** komut satırı seçeneklerinin ön eki olarak bir tire () kullanır, ancak bu konu eğik çizgi ( **/** ) kullanır. Her iki önek de kabul edilebilir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalManifestFiles**|İsteğe bağlı **dize []** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/MANIFEST** seçeneğine bakın.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi. Örneğin, "*/option1/option2/option #*". Başka bir **MT** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" başlığına bakın.|  
|**AssemblyIdentity**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimin **assemblyIdentity** öğesinin öznitelik değerlerini belirtir. İlk bileşen özniteliğin değeri, `name` ardından, * \<attribute name> =<attribute_value>* olan bir veya daha fazla ad/değer çifti olduğunda, virgülle ayrılmış bir liste belirtin.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/Identity** seçeneğine bakın.|  
|**ComponentFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> . Rgs veya. tlb dosyalarından oluşturmayı düşündüğünüz dinamik bağlantı kitaplığının adını belirtir. **RegistrarScriptFile** veya **TypeLibraryFile** MT görev parametrelerini belirtirseniz bu parametre gereklidir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/DLL** seçeneğine bakın.|  
|**Dependencyınformationfile**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirim aracına yönelik derleme bağımlılığı bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgi dosyasını belirtir.|  
|**EmbedManifest**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bildirim dosyasını derlemeye gömer. İse `false` , tek başına bildirim dosyası olarak oluşturulur.|  
|**Enabledpitanıma**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , uygulamayı DPI kullanan olarak işaretleyen bildirim bilgilerine ekler. DPı kullanan bir uygulama yazmak, bir kullanıcı arabiriminin çok çeşitli yüksek DPı ekran ayarları boyunca sürekli olarak iyi görünmesini sağlar.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesinde "yüksek DPI" konusuna bakın.|  
|**GenerateCatalogFiles**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , Katalog tanımı (. cdf) dosyaları oluşturur.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/makecdfs** seçeneğine bakın.|  
|**GenerateCategoryTags**|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` Kategori etiketlerinin oluşturulmasına neden olur. Bu parametre ise `true` , **ManifestFromManagedAssemblyMT** görev parametresinin de belirtilmesi gerekir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/category** seçeneğine bakın.|  
|**Inputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynaktan bildirim girin. _ \<file> [_**;** Biçiminde bir kaynak belirtin _[_ **#** _] Resource_id>] <_; burada isteğe bağlı `resource_id` parametre negatif olmayan, 16 bit bir sayıdır.<br /><br /> Hayır `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/ınputresource** seçeneğine bakın.|  
|**ManifestFromManagedAssembly**|İsteğe bağlı **dize** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/managedassemblyname** seçeneğine bakın.|  
|**Manifesttoıgnore**|İsteğe bağlı **dize** parametresi.<br /><br /> (Kullanılmıyor.)|  
|**OutputManifestFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Çıkış bildiriminin adını belirtir. Bu parametre atlanırsa ve üzerinde yalnızca bir bildirim işletilebilir, bu bildirim yerinde değiştirilir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/Out** seçeneğine bakın.|  
|**Outputresourcebildirimleri**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi belirtilen tanımlayıcıya sahip RT_MANIFEST türünde bir kaynağa çıkış. Kaynak, _ \<file> [_**;** _[_ **#** _] Resource_id>] <_; burada isteğe bağlı `resource_id` parametre negatif olmayan, 16 bit bir sayıdır.<br /><br /> Hayır `resource_id` belirtilirse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/outputresource** seçeneğine bakın.|  
|**RegistrarScriptFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kayıtsız COM bildirim desteği için kullanılacak kaydedici betiği (. RGS) dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/r GS** seçeneğine bakın.|  
|**ReplacementsFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaydedici betiği (. RGS) dosyasındaki değiştirilebilen dizelerin değerlerini içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/değiştirmeleri** seçeneğine bakın.|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Bildirimi proje çıkışına katıştırmak için kullanılan çıkış kaynakları dosyasını belirtir.|  
|**Kaynaklar**|İsteğe bağlı `ITaskItem[]` parametre.<br /><br /> Boşluklarla ayrılmış bildirim kaynak dosyalarının bir listesini belirtir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/MANIFEST** seçeneğine bakın.|  
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bağımlılık öğeleri olmayan bir bildirim oluşturur. Bu parametre ise `true` , **ManifestFromManagedAssemblyMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/nodependency** seçeneğine bakın.|  
|**SuppressStartupBanner**|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" bölümünde **/nologo** seçeneğine bakın.|  
|**TrackerLogDirectory**|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için İzleme günlüklerinin depolandığı ara dizini belirtir.|  
|**TypeLibraryFile**|İsteğe bağlı **dize** parametresi.<br /><br /> Tür kitaplığı (. tlb) dosyasının adını belirtir. Bu parametreyi belirtirseniz, **ComponentFileNameMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/tlb** seçeneğine bakın.|  
|**Updatefilekarmaları**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, **UpdateFileHashesSearchPathMT** görev parametresi tarafından belirtilen yoldaki dosyaların karma değerini hesaplar ve ardından Hesaplanan değeri kullanarak bildirimin **Dosya** öğesinin **karma** özniteliğinin değerini güncelleştirir.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" içindeki **/hashupdate** seçeneğine bakın. Ayrıca bkz. bu tablodaki **UpdateFileHashesSearchPath** parametresi.|  
|**UpdateFileHashesSearchPath**|İsteğe bağlı `String` parametre.<br /><br /> Dosya karmaları güncelleştirilirken kullanılacak arama yolunu belirtir. **UpdateFileHashesMT** görev parametresiyle bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için bu tablodaki **Updatefilekarmaları** parametresine bakın.|  
|**VerboseOutput**|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Ayrıntılı hata ayıklama bilgilerini görüntüler.<br /><br /> Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "Mt.exe" bölümündeki **/verbose** seçeneğine bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)

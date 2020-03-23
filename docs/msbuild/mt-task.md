---
title: MT Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633063"
---
# <a name="mt-task"></a>MT görevi

Microsoft Manifest Aracı, *mt.exe*sarar. Daha fazla bilgi için [Bkz. Mt.exe](/windows/desktop/SbsCs/mt-exe).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **MT** görevinin parametreleri açıklanmaktadır. Görev parametrelerinin çoğu ve birkaç parametre kümesi komut satırı seçeneğine karşılık gelir.

> [!NOTE]
> *mt.exe* dokümantasyonu komut**-** satırı seçenekleri için öneki olarak tire ( ) kullanır, ancak bu konu bir eğik çizgi kullanır ( ).**/** Her iki önek kabul edilebilir.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ek Manifesto Dosyaları**|İsteğe bağlı **String[]** parametresi.<br /><br /> Bir veya daha fazla bildirim dosyasının adını belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/manifest** seçeneğine bakın.|
|**Ek Seçenekler**|İsteğe bağlı **String** parametresi.<br /><br /> Komut satırı seçenekleri listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **MT** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [Bkz. Mt.exe](/windows/desktop/SbsCs/mt-exe).|
|**Assemblyıdentity**|İsteğe bağlı **String** parametresi.<br /><br /> Bildirimin **assemblyIdentity** öğesinin öznitelik değerlerini belirtir. İlk bileşenöz `name` öznitelik değeri, form, * \<öznitelik adı>=<attribute_value>* sahip bir veya daha fazla ad/değer çiftleri, ardından virgülle sınırlandırılmış bir liste belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/identity** seçeneğine bakın.|
|**ComponentFileName**|İsteğe bağlı **String** parametresi.<br /><br /> *.rgs* veya *.tlb* dosyalarından oluşturmak istediğiniz dinamik bağlantı kitaplığınadını belirtir. **RegistrarScriptFile** veya **TypeLibraryFile** MT görev parametrelerini belirtirseniz bu parametre gereklidir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/dll** seçeneğine bakın.|
|**BağımlılıkBilgiDosyası**|İsteğe bağlı **String** parametresi.<br /><br /> Bildirim aracıiçin yapı bağımlılık bilgilerini izlemek için Visual Studio tarafından kullanılan bağımlılık bilgileri dosyasını belirtir.|
|**EmbedManifest**|İsteğe bağlı `Boolean` parametre.<br /><br /> Bildirim `true`dosyasını derlemeye katıştırıyorsa. Eğer, `false`tek başına bir bildirim dosyası olarak oluşturur.|
|**EnableDPIAwareness**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`dpi-farkında olarak uygulama işaretleri bildirimdeki bilgilere ekler. DPI'ya duyarlı bir uygulama yazmak, kullanıcı arabiriminin çok çeşitli yüksek DPI ekran ayarlarında tutarlı bir şekilde iyi görünmesini sağlar.<br /><br /> Daha fazla bilgi için [Yüksek DPI'ya](/windows/desktop/win7devguide/high-dpi)bakın.|
|**Katalog Dosyaları Oluşturma**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, katalog tanımı oluşturur (*.cdf*) dosyaları.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/makecdfs** seçeneğine bakın.|
|**OluşturmaKategoriEtiketler**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`kategori etiketleri oluşturulmasına neden olur. Bu parametre `true`ise, **ManifestFromManagedAssemblyMT** görev parametresi de belirtilmelidir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/kategori** seçeneğine bakın.|
|**GirişKaynak Manifestoları**|İsteğe bağlı **String** parametresi.<br /><br /> Belirtilen tanımlayıcıya sahip tür RT_MANIFEST kaynağından bildirimi girin. Formun bir kaynağı \<belirtin, dosya>[;[ #]\<resource_id>], \<isteğe bağlı resource_id> parametresi negatif olmayan, 16 bitlik bir sayıdır.<br /><br /> Hayır `resource_id` belirtilmezse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/inputresource** seçeneğine bakın.|
|**ManifestFromManagedAssembly**|İsteğe bağlı **String** parametresi.<br /><br /> Belirtilen yönetilen derlemeden bir bildirim oluşturur.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/managedassemblyname** seçeneğine bakın.|
|**ManifesttoIgnore**|İsteğe bağlı **String** parametresi.<br /><br /> (Kullanılmaz.)|
|**OutputManifestFile**|İsteğe bağlı **String** parametresi.<br /><br /> Çıktı bildiriminin adını belirtir. Bu parametre atlanırsa ve yalnızca bir manifesto çalıştırılıyorsa, bu bildirim yerinde değiştirilir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/out** seçeneğine bakın.|
|**OutputResourceManifests**|İsteğe bağlı **String** parametresi.<br /><br /> Bildirimi belirtilen tanımlayıcıya sahip tür RT_MANIFEST kaynağına çıktın. Kaynak form, \<dosya>[;[ #]\<resource_id>], \<isteğe bağlı resource_id> parametresi negatif olmayan, 16 bitlik bir sayıdır.<br /><br /> Hayır `resource_id` belirtilmezse, CREATEPROCESS_MANIFEST_RESOURCE varsayılan değer (1) kullanılır.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/outputresource** seçeneğine bakın.|
|**RegistrarScriptFile**|İsteğe bağlı **String** parametresi.<br /><br /> Kayıt gerektirmeden COM bildirim desteği için kullanılacak kayıt defterinin *(.rgs)* dosyasını belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/rgs** seçeneğine bakın.|
|**YedeklerDosya**|İsteğe bağlı **String** parametresi.<br /><br /> Kayıt defteri komut dosyasındaki değiştirilebilir dizeleri *(.rgs)* dosyasıiçin değerleri içeren dosyayı belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/değiştirme** seçeneğine bakın.|
|**Kaynak ÇıktısıDosya Adı**|İsteğe bağlı **String** parametresi.<br /><br /> Bildirimi proje çıktısına yerleştirmek için kullanılan çıktı kaynakları dosyasını belirtir.|
|**Kaynak**|İsteğe bağlı `ITaskItem[]` parametre.<br /><br /> Boşluklara göre ayrılmış bildirim kaynağı dosyalarının listesini belirtir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/manifest** seçeneğine bakın.|
|**SuppressDependencyElement**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`bağımlılık öğeleri olmadan bir bildirim oluşturur. Bu parametre `true`ise, **ManifestFromManagedAssemblyMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/nodependency** seçeneğine bakın.|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı `String` parametre.<br /><br /> Bu görev için izleme günlüklerinin depolandığı ara dizini belirtir.|
|**TypeLibraryFile**|İsteğe bağlı **String** parametresi.<br /><br /> Tür kitaplığı (*.tlb*) dosyasının adını belirtir. Bu parametreyi belirtirseniz, **ComponentFileNameMT** görev parametresini de belirtin.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/tlb** seçeneğine bakın.|
|**GüncellemeFileHashes**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, **UpdateFileHashesSearchPathMT** görev parametresi tarafından belirtilen şekilde dosyaların karma değerini hesaplar ve sonra açılan değeri kullanarak manifestin **dosya** öğesinin **karma** özniteliği değerini güncelleştirir.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/hashupdate** seçeneğine bakın. Ayrıca bu tabloda **UpdateFileHashesSearchPath** parametrebakın.|
|**GüncellemeFileHashesSearchPath**|İsteğe bağlı `String` parametre.<br /><br /> Dosya güçlükleri güncelleştirildiğinde kullanılacak arama yolunu belirtir. Bu parametreyi **UpdateFileHashesMT** görev parametresi ile kullanın.<br /><br /> Daha fazla bilgi için bu tablodaki **UpdateFileHashes** parametresini görün.|
|**VerboseOutput**|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`ayrıntılı hata ayıklama bilgileri görüntüler.<br /><br /> Daha fazla bilgi için [Mt.exe'deki](/windows/desktop/SbsCs/mt-exe) **/verbose** seçeneğine bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)

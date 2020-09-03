---
title: Hata ayıklayıcıda sembol (. pdb) ve kaynak dosyaları belirtin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4d4b02d512480d96c501758f4cf0f1313158942
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300547"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Visual Studio Hata Ayıklayıcısında Simge (.pdb) ve Kaynak Dosyaları Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sembol dosyası olarak da bilinen program veritabanı (.pdb) dosyası sınıflar, yöntemler ve başka bir kod için kaynak dosyalarında oluşturduğunuz tanımlayıcıları projenizin derlenen yürütülebilir dosyalarında kullanılan tanımlayıcılarla eşleştirir. .Pdb dosyası, kaynak kodundaki deyimleri yürütülebilir dosyalardaki yürütme yönergeleriyle de eşleştirir. Hata ayıklayıcı iki temel bilgi parçasını belirlemek için bu bilgileri kullanır: Visual Studio IDE'sinde görüntülenen kaynak dosya ve satır numarası ile bir kesme noktası ayarladığınızda durdurulacak yürütülebilir öğenin konumu. Sembol dosyası ayrıca orijinal kaynak dosyası konumunu ve isteğe bağlı olarak, kaynak dosyasının alındığı kaynak sunucusunun konumunu içerir.

 Visual Studio IDE 'de bir projede hata ayıklarken, hata ayıklayıcı kodunuzun. pdb ve kaynak dosyaları için varsayılan konumu bilir. Proje çağrılarınızda Windows veya üçüncü taraf kodu olması gibi, proje kaynak kodunuz dışında kod hatası ayıklamak istiyorsanız, .pdb konumunu (ve isteğe bağlı olarak, harici kod kaynak dosyalarını) belirtmeniz gerekir ve bu dosyaların yürütülebilir yapıyla tam olarak eşleşmesi gerekir.

 Visual Studio 2012 ' den önce, simge dosyalarını uzak makineye yerleştirmeniz gereken uzak bir cihazda yönetilen koddan hata ayıklaması yaptığınızda. Bu durum artık geçerli değildir. Tüm sembol dosyaları yerel makinede veya **Araçlar/Seçenekler/hata ayıklama/Semboller** sayfasında belirtilen bir konumda bulunmalıdır.

## <a name="where-the-debugger-searches-for-pdb-files"></a><a name="BKMK_Find_symbol___pdb__files"></a> Hata ayıklayıcı. pdb dosyalarını arayacağı yer

1. DLL veya yürütülebilir dosyanın içinde belirtilen konum.

     (Varsayılan olarak, bilgisayarınızda bir DLL veya yürütülebilir dosya oluşturduysanız bağlayıcı, DLL veya yürütülebilir dosya içindeki ilgili .pdb dosyasının yolunu ve dosya adını tam olarak yerleştirir. Hata ayıklayıcı önce DLL'de veya yürütülebilir dosyada belirtilen konumda sembol dosyasının varolup olmadığını denetler. Her zaman bilgisayarınızda derlediğiniz kod için kullanılabilir semboller olduğundan bu yararlıdır.)

2. DLL veya yürütülebilir dosyayla aynı klasörde bulunabilecek .pdb dosyaları.

3. Yerel sembol önbellek klasörleri.

4. Etkinleştirildiyse Microsoft sembol sunucusu gibi sunucu üzerinde belirtilen tüm ağ, internet veya yerel sembol sunucuları ve konumları.

### <a name="why-do-symbol-files-need-to-exactly-match-the-executable-files"></a><a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Sembol dosyalarının yürütülebilir dosyalarla neden tam olarak eşleşmesi gerekir?
 Hata ayıklayıcı, yalnızca yürütülebilir dosya oluşturulduğunda, oluşturulan .pdb dosyasıyla tam olarak eşleşen bir yürütülebilir dosya için bir .pdb dosyasını yükler (yani, .pdb özgün olmalı veya özgün .pdb'nin kopyasını olmalıdır). Doğru ve verimli kod oluşturma olan temel görevinin yanı sıra derleyici derleme hızı için de optimize edilmiş olduğundan, kodun kendisi değişmese bile yürütülebilir dosyanın gerçek düzeni değişebilir. Daha fazla bilgi için bkz. [Visual Studio neden hata ayıklayıcı sembol dosyalarının ile derlendikleri ikili dosyalarla tam olarak eşleşmesi gerekir?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

### <a name="specify-symbol-locations-and-loading-behavior"></a><a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Sembol konumları ve yükleme davranışı belirtin
 VS IDE içinde bir projede hata ayıklaması yaparken, hata ayıklayıcı proje dizininde yer alan sembol dosyalarını otomatik olarak yükler. **Araçlar/Seçenekler/hata ayıklama/Semboller**içinde Microsoft, Windows veya üçüncü taraf bileşenleri için alternatif arama yolları ve sembol sunucuları belirtebilirsiniz. Ayrıca, hata ayıklayıcının sembolleri otomatik olarak yüklemesini istediğiniz belirli modülleri de belirtebilirsiniz. Ve daha sonra etkin bir şekilde hata ayıklama yaparken bu ayarları el ile değiştirebilirsiniz.

1. Visual Studio 'da **Araçlar/Seçenekler/hata ayıklama/Semboller** sayfasını açın.

    ![Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Klasör ![araçlar&#47; seçenekler&#47; hata ayıklama&#47;semboller klasörü simgesi](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") simgesine tıklayın. Düzenlenebilir metin **sembol dosyası (. pdb) konumları** kutusunda görünür.

3. URL'yi ya da sembol sunucusunun veya sembol konumunun dizin yolunu yazın. Deyimi tamamlama doğru biçimi bulmanıza yardımcı olur.

4. Sembol yükleme performansını artırmak için, bu dizin kutusunda simgelerin kopyalanabilecek yerel bir dizin olan **Bu dizindeki önbellek sembollerinin** sembol sunucuları tarafından kopyalanabilecek yerel bir dizinin yolunu yazın.

   > [!NOTE]
   > Sembol önbelleğinizi korunan klasöre (C:\Windows folder veya bunun alt klasörlerinden biri) koymayın. Bunun yerine okuma-yazma klasörü kullanın.

   **Sembol yükleme davranışı belirtin**

   Hata ayıklamaya başladığınızda **sembol dosyası (. pdb) konumları** kutusu konumlarından otomatik olarak yüklenmesini istediğiniz dosyaları belirtebilirsiniz. Proje dizinindeki sembol dosyaları her zaman yüklenir.

5. **Dışlanan modülleri belirt** bağlantısını seçtiğinizde belirtmediğiniz durumlar dışındaki tüm modüller için tüm sembolleri yüklemek dışında **tutulmadığı sürece tüm modüller ' i** seçin.

6. **Yalnızca belirtilen modüller** seçeneğini belirleyin ve ardından otomatik olarak yüklenmesini istediğiniz sembol dosyalarını listelemek Için **modülleri belirt** ' i seçin. Diğer modüller için sembol dosyaları göz ardı edilir.

   **Ek sembol seçeneklerini belirtin**

   **Araçlar/Seçenekler/hata ayıklama/Semboller** sayfasında aşağıdaki seçenekleri de ayarlayabilirsiniz:

   **Başlatma üzerinde hiçbir sembol yoksa uyar (yalnızca yerel)**

   Seçilirse, hata ayıklayıcının kendisiyle ilgili sembole yönelik bilgi içermediği bir programdaki hataları ayıklamayı denediğinizde bir uyarı iletişim kutusu görüntüler.

   **DLL dışarı aktarmaları yükle**

   Seçildiğinde, DLL dışa aktarma tablolarını yükler. DLL dışa aktarma tablolarının sembole yönelik bilgileri, Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri veya sıralama ile ya da sembolleri olmayan herhangi bir DLL ile çalışıyorsanız yararlı olabilir. DLL dışa aktarma bilgilerini okuma bazı ek okumalar içerir. Bu nedenle, bu özellik varsayılan olarak kapalıdır.

   DLL 'nin dışarı aktarma tablosunda hangi simgelerin kullanılabildiğini görmek için kullanın `dumpbin /exports` . Semboller tüm 32-bit sistem DLL için kullanılabilir. Çıktıyı okuyarak, `dumpbin /exports` alfasayısal olmayan karakterler de dahil olmak üzere tam işlev adını görebilirsiniz. Bu, bir işlev bir kesme noktası ayarlamak için yararlıdır. DLL dışarı aktarma tablolarındaki işlev adları, hata ayıklayıcının başka bir yerinde kesilmiş görünebilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir. Daha fazla bilgi için bkz. [dumpbin/dışarı aktarmalar](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

### <a name="use-symbol-servers-to-find-symbol-files-not-on-your-local-machine"></a><a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Yerel makinenizde bulunmayan sembol dosyalarını bulmak için sembol sunucularını kullanın
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , symsrv protokolünü uygulayan sembol sunucularından hata ayıklama sembol dosyalarını indirebilir. [Visual Studio Team Foundation Server](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) ve [Windows Için hata ayıklama araçları](https://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) , sembol sunucularını uygulayabilirler iki araç. VS **seçenekleri** iletişim kutusunda kullanılacak sembol sunucularını belirtirsiniz.

 Kullanabileceğiniz sembol sunucuları şunlardır:

 **Microsoft genel sembol sunucuları**

 Bir sistem DLL dosyasına veya bir üçüncü taraf kitaplığına yapılan bir çağrı sırasında oluşan bir çökme hatasını gidermek için, genellikle Windows DLL'leri, EXE'ler, ve cihaz sürücüleri için semboller içeren .pdb dosyalarına gereksinim duyarsınız. Bu sembolleri Microsoft ortak sembol sunucularından elde edebilirsiniz. Microsoft genel sembol sunucuları, MDAC, IIS, ISA ve ' nin yanı sıra Windows işletim sistemlerine yönelik simgeler sağlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

 Microsoft sembol sunucularını kullanmak için, **hata ayıklama** menüsünde **Seçenekler ve ayarlar** ' ı seçin ve ardından **semboller**' i seçin. **Microsoft sembol sunucuları**' nı seçin.

 **Bir iç ağdaki veya yerel makinenizdeki sembol sunucuları**

 Ekibiniz veya şirketiniz, kendi ürünleriniz için ve dış kaynaklardan alınan sembollerin önbelleği olarak sembol sunucuları oluşturabilir. Kendi makineniz üzerinde bir sembol sunucusu olabilir. Sembol sunucularının konumunu bir URL olarak veya **Debugging** / vs **seçeneği iletişim kutusunun**hata ayıklama**sembolleri** sayfasında bir yol olarak girebilirsiniz.

 **Üçüncü taraf sembol sunucuları**

 Üçüncü taraf Windows uygulamaları ve kitaplıkları sağlayıcılar internet üzerinden sembol sunucusuna erişim sağlayabilir. Ayrıca, **hata ayıklama** / **sembolleri** sayfasında bu sembol sunucularının URL 'sini de girersiniz.

> [!NOTE]
> Microsoft ortak sembol sunucularından farklı bir sembol sunucusu kullanıyorsanız, sembol sunucusunun ve yolunun güvenilir olduğundan emin olun. Sembol dosyası rastgele yürütülebilir kod içerebileceğinden güvenlik tehditlerine maruz kalabilirsiniz.

### <a name="find-and-load-symbols-while-debugging"></a><a name="BKMK_Find_and_load_symbols_while_debugging"></a> Hata ayıklama sırasında sembolleri bulma ve yükleme
 Hata ayıklayıcı kesme modundayken, hata ayıklayıcı seçenekleriyle daha önce hariç tutulan veya derleyicinin bulamadığı bir modül için semboller yükleyebilirsiniz. Çağrı Yığını, Modüller, Yereller, Otolar ve tüm Gözcü pencerelerinin kısayol menülerinden sembol yükleyebilirsiniz. Hata ayıklayıcısı sembol veya kaynak dosyalarına sahip olmayan kodu keserse, bir belge penceresi görüntülenir. Burada, eksik dosyaları ve bunları bulup yüklemek için yapılacak eylemler hakkında bilgi bulabilirsiniz.

 **Sembol yüklü olmayan sembolleri bul belge sayfaları**

 Hata ayıklayıcının kullanılabilir sembolleri bulunmayan kodlara girebilmesi için çeşitli yollar vardır:

1. Kodun içine adımlama.

2. Kodu kesme noktasından veya özel durumdan ayırma.

3. Farklı bir iş parçacığına geçiş.

4. Çağrı Yığını penceresinde bir çerçeveyi çift tıklayarak yığın çerçevesini değiştirme.

   Bu olaylardan biri oluştuğunda, hata ayıklayıcı gerekli sembolleri bulmanıza ve yüklemeye yardımcı olması için **simge yüklü değil** sayfasını görüntüler.

   ![Simge yüklenmedi sayfası yok](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Arama yollarını değiştirmek için, seçilmeyen bir yolu seçin veya **Yeni** ' yi seçip yeni bir yol girin. Yolları tekrar aramak ve bulunursa sembol dosyasını yüklemek için **Yükle** ' yi seçin.

- Herhangi bir sembol seçeneklerini geçersiz kılmak ve arama yollarını yeniden denemek için, **Gözden geçirme ve**_yürütülebilir dosya adı_**..** . seçeneğini belirleyin. Sembol dosyası bulunursa yüklenir veya sembol dosyasını el ile seçmeniz için bir Dosya Gezgini görüntülenir.

- VS seçenekleri iletişim kutusunun **hata ayıklama**sembolleri sayfasını göstermek için **sembol ayarlarını değiştir...** seçeneğini belirleyin  /  **Symbols** .

- Ayrıştırılmış derlemeyi yeni bir pencerede bir kez göstermek için **ayrıştırılmış derlemeyi görüntüle** ' yi seçin.

- Kaynak veya sembol dosyaları bulunamadığında ayrıştırılmış kodu her zaman göstermek için, **Seçenekler iletişim kutusu** bağlantısını seçin ve **Adres düzeyi hata ayıklamayı etkinleştir** ' i seçin ve **Kaynak kullanılamıyorsa ayrıştırılmış derlemeyi gösterin**.

   ![Seçenekler &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Kısayol menüsünden sembol seçeneklerini değiştirme**

  Kesme modunda çalışırken, Çağrı Yığını, Modüller, Yerel Öğeler, Otomatik Öğeler ve tüm İzleme pencerelerinde görüntülenen öğelerin sembollerini bulabilir ve yükleyebilirsiniz. Pencerede bir öğe seçin, kısayol menüsünü açın ve aşağıdaki seçeneklerden birini seçin:

|Seçenek|Açıklama|
|------------|-----------------|
|**Sembolleri yükle**|Seçenekler iletişim kutusunun **hata ayıklama**  /  **sembolleri** sayfasında belirtilen konumlardan sembolleri yüklemeye çalışır. **Options** Sembol dosyası bulunamazsa, Dosya Gezgini başlatılır, bu sayede aranacak yeni bir konum belirtebilirsiniz.|
|**Sembol Yükleme Bilgisi**|Yüklenen sembol dosyasının konumunu veya hata ayıklayıcı dosyasını bulamazsanız, aranan konumları gösteren bilgiler sunar.|
|**Sembol ayarları...**|VS seçenekleri iletişim kutusunun **hata ayıklama**  /  **sembolleri** sayfasını **Options** açar.|
|**Her zaman otomatik olarak yükle**|Hata ayıklayıcı tarafından otomatik yüklenen dosya listesine sembol dosyası ekler.|

### <a name="set-compiler-options-for-symbol-files"></a><a name="BKMK_Set_compiler_options_for_symbol_files"></a> Sembol dosyaları için derleyici seçeneklerini ayarla
 Projenizi VS IDE 'den yapılandırdığınızda ve standart **hata ayıklama** yapı yapılandırmasını kullandığınızda, C++ ve yönetilen derleyiciler kodunuz için uygun semboller dosyalarını oluşturur. Sembol dosyaları oluşturmak için komut satırında derleyici seçeneklerini de ayarlayabilirsiniz.

 **C++ seçenekleri**

 Program veritabanı (.pdb) dosyası, hata ayıklamayı ve programınızın Hata ayıklama yapılandırmasının artımlı bağlamasına olanak tanıyan proje durum bilgilerini tutar. [/Zi veya/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) ile oluşturduğunuzda bir. pdb dosyası oluşturulur (C/C++ için).

 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]' De, [/FD](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) seçeneği derleyici tarafından oluşturulan. pdb dosyasını adlandırır. Sihirbazları kullanarak bir proje oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **/FD** seçeneği *Project*. pdb adlı bir. pdb dosyası oluşturmak üzere ayarlanır.

 C/C++ uygulamanızı bir Makefile kullanarak oluşturursanız ve **/Zi** veya **/Zi** 'yi **/FD**olmadan belirtirseniz, iki. pdb dosyası ile biter:

- VC*x*. pdb, burada *x* , Visual C++ sürümünü temsıl eder, örneğin VC11. pdb. Bu dosya, tek tek OBJ dosyaları için hata ayıklama bilgilerini depolar ve proje derleme görevleri dosyası ile aynı dizinde bulunur.

- Project. pdb bu dosya the.exe dosya için tüm hata ayıklama bilgilerini depolar. C/C++'ta \debug alt dizininde bulunur.

  Bir OBJ dosyası her oluşturduğunda, C/C++ derleyicisi hata ayıklama bilgilerini VC*x*. pdb ile birleştirir. Eklenen bilgiler türü bilgilerini içerir, ancak işlev tanımları gibi sembol bilgilerini içermez. Her kaynak dosya gibi ortak üst bilgi dosyalarını içerse de \<windows.h> , bu başlıklardan tür tanımları her obj dosyasında olmak yerine yalnızca bir kez depolanır.

  Bağlayıcı, projenin EXE dosyasına ilişkin hata ayıklama bilgilerini içeren project.pdb'yi oluşturur. Project. pdb dosyası, yalnızca VC*x*. pdb 'de bulunan tür bilgilerini değil, işlev prototipleri dahil olmak üzere tam hata ayıklama bilgileri içerir. Her iki .pdb dosyası da artımlı güncelleştirmelere izin verir. Bağlayıcı ayrıca .pdb dosyasının yolunu, oluşturduğu .exe veya .dll dosyasına katıştırır.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı, Project. pdb dosyasını bulmak IÇIN exe veya dll dosyasında. pdb dosyasının yolunu kullanır. Hata ayıklayıcı, bu konumda. pdb dosyasını bulamazsa veya yol geçersizse (örneğin, proje başka bir bilgisayara taşınmışsa), hata ayıklayıcı EXE içeren yolu, **Seçenekler** iletişim kutusunda (**hata ayıklama** klasörü, **semboller** düğümü) belirtilen sembol yollarını arar. Hata ayıklayıcı, hata ayıklaması yapılan yürütülebilir öğeyle eşleşmeyen bir .pdb dosyası yüklemez. Hata ayıklayıcı bir. pdb dosyası bulamazsa, sembolleri aramanızı veya arama yoluna ek konumlar eklemenizi sağlayan bir **sembol bul** iletişim kutusu görüntülenir.

  **.NET Framework seçenekleri**

  Program veritabanı (.pdb) dosyası, hata ayıklamayı ve programınızın hata ayıklama yapılandırmasının artımlı bağlamasına olanak tanıyan proje durum bilgilerini tutar. **/Debug**ile derleme yaptığınızda bir. pdb dosyası oluşturulur. **/Debug: Full** veya **/Debug: pdbonly**ile uygulamalar oluşturabilirsiniz. **/Debug: Full** ile derleme hata ayıklanabilir kodu oluşturur. **/Debug: pdbile derleme yalnızca** . pdb dosyaları oluşturur, ancak `DebuggableAttribute` JIT derleyicisine hata ayıklama bilgilerinin kullanılabildiğini söyleyen öğesini oluşturmaz. Hata ayıklanabilir olmasını istemediğiniz bir yayın derlemesi için. pdb dosyaları oluşturmak istiyorsanız **/Debug: pdbonly** kullanın. Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) veya [/Debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Hata ayıklayıcı, Project. pdb dosyasını bulmak IÇIN exe veya dll dosyasında. pdb dosyasının yolunu kullanır. Hata ayıklayıcı, bu konumda. pdb dosyasını bulamazsa veya yol geçersizse, hata ayıklayıcı EXE içeren yolu arar ve ardından **Seçenekler** iletişim kutusunda belirtilen sembol yollarını arar. Bu yol genellikle **semboller** düğümündeki **hata ayıklama** klasörüdür. Hata ayıklayıcı, hata ayıklaması yapılan yürütülebilir dosyayla eşleşmeyen bir .pdb dosyası yüklemez. Hata ayıklayıcı bir. pdb dosyası bulamazsa, sembolleri aramanızı veya arama yoluna ek konumlar eklemenizi sağlayan bir **sembol bul** iletişim kutusu görüntülenir.

  **Web uygulamaları**

  Uygulamanızın yapılandırma dosyası (Web.config) hata ayıklama moduna ayarlanmalıdır. Hata ayıklama modu ASP.NET'in dinamik olarak oluşturulan dosyalar için sembol oluşturmasına neden olur ve hata ayıklayıcının ASP.NET uygulamasına eklemesine olanak tanır. Web Proje şablonunu kullanarak projenizi oluşturduysanız, hata ayıklamayı başlattığınızda VS bunu otomatik olarak ayarlar.

## <a name="find-source-files"></a><a name="BKMK_Find_source_files"></a> Kaynak dosyaları bul

### <a name="where-the-debugger-searches-for-source-files"></a><a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Hata ayıklayıcının kaynak dosyalarını arayacağı yer
 Hata ayıklayıcı kaynak dosyaları aşağıdaki konumlarda arar:

1. Hata ayıklayıcı tarafından başlatılan Visual Studio örneğinin IDE'si içinde açık olan dosyalar.

2. Visual Studio örneğinde açık olan çözümdeki dosyalar.

3. Çözüm özelliklerindeki **ortak özellikler**  /  **hata ayıklama kaynak dosyaları** sayfasında belirtilen dizinler. ( **Çözüm Gezgini**çözüm düğümünü seçin, sağ tıklayın ve **Özellikler**' i seçin. )

4. Modülün .pdb dosyasının kaynak bilgisi. Bu, modül oluşturulduğunda kaynak dosyanın konumu olabileceği gibi, bir kaynak sunucuya ilişkin komut da olabilir.

### <a name="find-and-load-source-files-with-the-no-source--no-symbols-loaded-pages"></a><a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Kaynak/sembol yüklenmemiş bir sayfa ile kaynak dosyalarını bulun ve yükleyin
 Hata ayıklayıcı, kaynak dosyanın kullanılamadığı bir konumda yürütmeyi kesintiye böldüğünde, kaynak dosyayı bulmanıza yardımcı olabilecek **hiçbir kaynak yüklenmemiş** veya **simge yüklü** olmayan sayfa yok görüntülenir. Hata ayıklayıcı, arama işleminin tamamlanabilmesi için yürütülebilir dosya için bir simge (. pdb) dosyası bulamadığında **hiçbir sembol yüklenmedi** görüntülenir. Sembol Yok sayfası dosyayı aramak için seçenekler sağlar. Seçeneklerden birini çalıştırdıktan sonra .pdb bulunursa ve hata ayıklayıcı semboller dosyasındaki bilgileri kullanarak kaynak dosyayı alırsa, kaynak görüntülenir. Aksi halde, sorunu açıklayan, **kaynak yüklenmemiş** bir sayfa görüntülenir. Sayfa, sorunu giderebilecek eylemleri gerçekleştirebilen seçenek bağlantıları görüntüler.

### <a name="add-source-file-search-paths-to-a-solution"></a><a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Bir çözüme kaynak dosya arama yolları ekleme
 Kaynak dosyalarını aramak için ağ veya yerel dizin belirtebilirsiniz.

1. Çözüm Gezgini içinde çözümü seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

2. **Ortak özellikler** düğümünde **Hata Ayıkla kaynak dosyaları**' nı seçin.

3. Klasör ![araçları&#47; seçenekler&#47; hata ayıklama&#47;semboller klasörü simgesi](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") simgesine tıklayın. Düzenlenebilir metin, **kaynak kodu Içeren dizinler** listesinde görünür.

4. Aramak istediğiniz yolu ekleyin.

   Yalnızca belirtilen dizin arandığına dikkat edin. Arama yapmak istediğiniz alt dizinler için girdi eklemeniz gerekir.

### <a name="use-source-servers"></a><a name="BKMK_Use_source_servers"></a> Kaynak sunucuları kullanma
 Yerel makinede kaynak kod olmadığında veya .pdb dosyası kaynak kodla eşleşmediğinde, uygulamada hata ayıklamaya yardımcı olması için Kaynak Sunucuyu kullanabilirsiniz. Kaynak Sunucu, dosya isteklerini alır ve gerçek dosyaları döndürür. Kaynak Sunucu, srcsrv.dll adlı bir DLL dosyası ile çalışır. Kaynak Sunucu, kaynak kodu depodan almak için kullanılan komutların yanı sıra kaynak kodu deposuna işaretçiler içeren uygulamanın .pdb dosyasını okur. devenv.exe ve srcsrv.dll ile aynı dizine konması gereken srcsrv.ini adlı dosyadaki izin verilen komutları listeleyerek hangi komutlara uygulamanın .pdb dosyasından yürütülmesini izin verileceğini sınırlayabilirsiniz.

> [!IMPORTANT]
> Rastgele komutlar uygulamanın .pdb dosyasına katıştırılabildiğinden yalnızca yürütmek istediğiniz komutları srcsrv.ini dosyasına koyduğunuzdan emin olun. srcsvr.ini dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için bkz. [güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, cmd.exe'ye güvendiyseniz, kötü niyetli bir kullanıcı, komutu tehlikeli duruma getirecek parametreler belirtebilir.

 **Kaynak sunucu kullanımını etkinleştirmek için**

1. Önceki bölümde açıklanan güvenlik önlemleri ile derlediğinizden emin olun.

2. **Araçlar** menüsünde **Seçenekler**' i seçin.

     **Seçenekler** iletişim kutusu görüntülenir.

3. **Hata ayıklama** düğümünde **genel**' i seçin.

4. **Kaynak sunucu desteğini etkinleştir** onay kutusunu seçin.

     ![Kaynak sunucu seçeneklerini etkinleştir](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5. (İsteğe bağlı) İstediğiniz alt seçeneği belirleyin.

     Hem **kısmi güven derlemeleri (yalnızca yönetilen) için kaynak sunucuya Izin ver** hem de **Güvenilmeyen kaynak sunucu komutlarını her zaman sormadan Çalıştır** , yukarıda açıklanan güvenlik risklerini artırabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 2012 ve 2013 ' de .NET uzak sembol yükleme değişiklikleri](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)

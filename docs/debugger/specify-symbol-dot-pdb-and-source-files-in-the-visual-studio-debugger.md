---
title: Hata ayıklayıcıda sembol (. pdb) ve kaynak dosyaları ayarlama
description: Visual Studio sembol ve kaynak dosyalarını yapılandırma ve yönetme hakkında bilgi edinin
ms.custom: ''
ms.date: 3/31/2021
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ee8f82fdc1e93e74e1dfc5fba99bb01576a583ea
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636606"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme (C#, C++, Visual Basic, F #)

Sembol dosyaları olarak da bilinen program veritabanı (*. pdb*) dosyaları, projenizin kaynak kodundaki derleme tanımlayıcıları ve deyimleri, derlenmiş uygulamalardaki karşılık gelen tanımlayıcılarla ve yönergeleriyle eşleştirin. Bu eşleme dosyaları hata ayıklayıcıyı kaynak kodunuza bağlar ve bu da hata ayıklamayı sağlar.

standart hata ayıklama yapı yapılandırmasıyla Visual Studio ıde 'den bir proje oluşturduğunuzda, derleyici uygun sembol dosyalarını oluşturur. Bu makalede, IDE 'de sembol dosyalarının nasıl yönetileceği, örneğin [hata ayıklayıcı seçeneklerinde simgelerin konumunu belirtme](#BKMK_Specify_symbol_locations_and_loading_behavior), hata ayıklama sırasında [sembol yükleme durumunun nasıl denetleneceği](#work-with-symbols-in-the-modules-window) ve [koddaki sembol seçeneklerinin nasıl ayarlanacağı](#compiler-symbol-options)açıklanır.

Sembol dosyalarının ayrıntılı bir açıklaması için aşağıdakilere bakın:

- [sembol dosyalarını ve Visual Studio sembol ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Visual Studio neden hata ayıklayıcı sembol dosyalarının, derlendikleri ikili dosyalarla tam olarak eşleşmesi gerekir?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Sembol dosyaları nasıl çalışır?

*. Pdb* dosyası, hata ayıklamayı ve uygulamanızın hata ayıklama yapılandırmasının artımlı bağlamasını sağlayan proje durum bilgilerini barındırır. Visual Studio hata ayıklayıcı, hata ayıklama sırasında iki temel bilgi parçasını belirlemede *. pdb* dosyalarını kullanır:

* Visual Studio ıde 'de görüntülenecek kaynak dosya adı ve satır numarası.
* Uygulamanın kesme noktası için durdurulması gereken yer.

Sembol dosyaları aynı zamanda kaynak dosyaların konumunu ve isteğe bağlı olarak, üzerinden alınacak sunucuyu da gösterir.

Hata ayıklayıcı yalnızca bir uygulama oluşturulduğunda oluşturulan *. pdb dosyalarıyla* tam olarak eşleşen *.* pdb dosyalarını yükler (yani, özgün *. pdb* dosyaları veya kopyalardır). Bu [tam yineleme](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) gereklidir çünkü bu, kodun kendisi değişmemiş olsa bile uygulamaların düzeni değişebilir.

> [!TIP]
> proje kaynak kodunuzun dışındaki kodun hatalarını ayıklamak için, Windows kodu veya projenizin çağrı kodu gibi, uygulamanızdaki derlemeleriyle tam olarak eşleşmesi gereken dış kodun *. pdb* dosyalarının (ve isteğe bağlı olarak kaynak dosyalarının) konumunu belirtmeniz gerekir.

## <a name="symbol-file-locations-and-loading-behavior"></a>Sembol dosya konumları ve yükleme davranışı

Visual Studio ıde 'de bir projede hata ayıklarken, hata ayıklayıcı proje klasöründe bulunan sembol dosyalarını otomatik olarak yükler.

> [!NOTE]
> Uzak bir cihazda yönetilen kodda hata ayıklarken, tüm sembol dosyaları yerel makinede ya da [hata ayıklayıcı seçeneklerinde belirtilen](#BKMK_Specify_symbol_locations_and_loading_behavior)bir konumda bulunmalıdır.

Hata ayıklayıcı Ayrıca sembol dosyalarını aşağıdaki konumlarda arar:

1. DLL veya çalıştırılabilir (*.exe*) dosyası içinde belirtilen konum.

   Varsayılan olarak, bilgisayarınızda bir DLL veya *.exe* dosyası oluşturduysanız BAĞLAYıCı, dll veya *.exe* dosyasına ilişkili *. pdb* dosyasının tam yolunu ve dosya adını koyar. Hata ayıklayıcı, sembol dosyasının bu konumda bulunup bulunmadığını denetler.

2. DLL veya *.exe* dosyası ile aynı klasör.

3. Sembol dosyaları için hata ayıklayıcı seçeneklerinde belirtilen konumlar. Sembol konumları eklemek ve etkinleştirmek için bkz. [simge konumlarını yapılandırma ve seçenekleri yükleme](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Herhangi bir yerel sembol önbellek klasörü.

   - Belirtilen ağ, internet veya yerel sembol sunucuları ve konumları (seçilmişse, Microsoft sembol sunucuları gibi). [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , protokolü uygulayan sembol sunucularından hata ayıklama sembol dosyalarını indirebilir `symsrv` . Windows için [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) ve [hata ayıklama araçları](/windows-hardware/drivers/debugger/index) , sembol sunucularını kullanan iki araç olabilir.

     Kullanabileceğiniz sembol sunucuları şunlardır:

     **Genel Microsoft sembol sunucuları**: sistem dll 'sine veya üçüncü taraf kitaplığına yapılan bir çağrı sırasında oluşan kilitlenmeyle ilgili hata ayıklamak için, genellikle System *. pdb* dosyalarına ihtiyacınız vardır. System *. pdb* dosyaları Windows dll 'ler, *.exe* dosyaları ve cihaz sürücüleri için semboller içerir. ortak Microsoft sembol sunucularından Windows işletim sistemleri, MDAC, ııs, ısa ve .net için semboller edinebilirsiniz.

     **Bir iç ağdaki veya yerel makinenizdeki sembol sunucuları**: ekibiniz veya şirketiniz, kendi ürünleriniz için sembol sunucuları ve dış kaynaklardan semboller için önbellek olarak oluşturabilir. Kendi makineniz üzerinde bir sembol sunucusu olabilir.

     **üçüncü taraf sembol sunucuları**: Windows uygulamaların ve kitaplıkların üçüncü taraf sağlayıcıları, ınternet 'teki sembol sunucusuna erişim sağlayabilir.

     > [!WARNING]
     > Ortak Microsoft sembol sunucularından farklı bir sembol sunucusu kullanıyorsanız, sembol sunucusunun ve yolunun güvenilir olduğundan emin olun. Sembol dosyaları rastgele yürütülebilir kod içerebildiğinden, güvenlik tehditlerine maruz olabilirsiniz.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Sembol konumlarını yapılandırma ve seçenekleri yükleme

**Araç**  >  **seçenekleri**  >  **hata ayıklama**  >  **sembolleri** sayfasında şunları yapabilirsiniz:

- Microsoft, Windows veya üçüncü taraf bileşenleri için arama yollarını ve sembol sunucularını belirtin ve seçin.
- Hata ayıklayıcının, için sembolleri otomatik olarak yüklemesini istediğiniz modülleri belirtin.
- Etkin bir şekilde hata ayıklarken bu ayarları değiştirin. Bkz. [hata ayıklama sırasında sembolleri yönetme](#manage-symbols-while-debugging).

**Sembol konumlarını ve yükleme seçeneklerini belirtmek için:**

1. Visual Studio, **araçlar**  >  **seçeneklerini**  >  **hata ayıklama**  >  **sembolleri** (veya **hata ayıklama**  >  **seçenekleri**  >  **sembolleri**) açın.

2. **Sembol dosyası (. pdb) konumları** altında,
   - **Microsoft Symbol sunucularını** veya **NuGet. org sembol sunucusunu** kullanmak için onay kutusunu seçin.

   - Yeni bir sembol sunucusu konumu eklemek için
     1. **+** Araç çubuğundan sembolünü seçin.
     1. URL (http), ağ paylaşma veya sembol sunucusunun yerel yolunu veya metin alanına sembol konumunu yazın. Deyimi tamamlama doğru biçimi bulmanıza yardımcı olur.

     ![Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası](media/dbg-options-symbols.gif "Araçlar &#45; Seçenekler &#45; Simgeler sayfasında &#45; Ayıklama")

     >[!NOTE]
     >Yalnızca belirtilen klasör aranır. Aramak istediğiniz alt klasörler için girdi eklemeniz gerekir.

   - Yeni bir VSTS sembol sunucusu konumu eklemek için
     1. Araç çubuğundaki ![araçlar&#47; seçenekler&#47; hata ayıklama&#47;simgeler yeni sunucu simgesi](media/dbg_tools_options_foldersicon.png "Tools &#45; Options &#45; Debugging &#45; Symbols new server icon") simgesini seçin.
     1. **VSTS 'ye Bağlan sembol sunucusu** iletişim kutusunda, kullanılabilir sembol sunucularından birini seçin ve **Bağlan**' ı seçin.

   - Sembol konumlarının yüklenme sırasını değiştirmek için **CTRL** + **yukarı** ve **CTRL** + **tuşlarını** ya da **yukarı** ve **aşağı** ok simgelerini kullanın.
   - Bir URL veya yolu düzenlemek için, girişe çift tıklayın veya seçin ve **F2** tuşuna basın.
   - Bir girişi kaldırmak için, seçin ve ardından **-** simgesini seçin.

3. Seçim Sembol yükleme performansını artırmak için, **Bu dizindeki önbellek sembolleri** altında, sembol sunucularının sembolleri kopyalayabilecek bir yerel klasör yolu yazın.

   > [!NOTE]
   > yerel sembol önbelleğini c:\ Windows veya alt klasör gibi korumalı bir klasöre yerleştirmeyin. Bunun yerine okuma-yazma klasörü kullanın.

   > [!NOTE]
   > C++ projeleri için, `_NT_SYMBOL_PATH` ortam değişkeni ayarlandıysa, **Bu dizindeki önbellek sembolleri** altında ayarlanan değeri geçersiz kılar.

4. Hata ayıklayıcının, başlatıldığında **sembol dosyası (. pdb) konumlarından** yüklenmesini istediğiniz modülleri belirtin.

   - Özel olarak hariç tutmadığınız modüller dışında sembol dosyası konumundaki tüm modüller için tüm sembolleri yüklemek üzere **dışlanmamışsa, tüm modülleri Yükle ' yi** seçin (varsayılan). Belirli modülleri dışlamak için **hariç tutulan modülleri belirt**' i seçin, **+** simgesini seçin, dışlanacak modüllerin adlarını yazın ve **Tamam**' ı seçin.

   - Yalnızca sembol dosya konumlarından belirttiğiniz modülleri yüklemek için **yalnızca belirtilen modülleri yükle**' yi seçin. **Dahil edilen modülleri belirt**' i seçin, **+** simgesini seçin, eklenecek modüllerin adlarını yazın ve ardından **Tamam**' ı seçin. Diğer modüllerin sembol dosyaları yüklü değil.

5. **Tamam**’ı seçin.

## <a name="other-symbol-options-for-debugging"></a>Hata ayıklama için diğer sembol seçenekleri

**Araç**  >  **seçeneklerinde**  >  **hata ayıklama**  >  **genel** (veya **hata ayıklama**  >  **seçenekleri**  >  **genel**) bölümünde ek sembol seçenekleri belirleyebilirsiniz:

- **DLL dışarı aktarmaları yükle (yalnızca yerel)**

  C/C++ için DLL dışa aktarma tablolarını yükler. Ayrıntılar için bkz. [DLL dışarı aktarma tabloları](#use-dumpbin-exports). DLL dışa aktarma bilgilerini okuma bazı ek yük içerir, bu nedenle dışarı aktarma tablolarının yüklenmesi varsayılan olarak kapalıdır. `dumpbin /exports`C/C++ yapı komut satırında de kullanabilirsiniz.

- **Adres düzeyinde hata ayıklamayı etkinleştir** ve **Kaynak kullanılamıyorsa ayrıştırılmış derlemeyi göster**

  Kaynak veya sembol dosyaları bulunamadığında, her zaman ayrıştırılmış kodu gösterir.

  ![Seçenekler &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri](../debugger/media/dbg_options_general_disassembly_checkbox.png "Genel &#47; seçenekleri &#47; hata ayıklama seçenekleri")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Kaynak sunucu desteğini etkinleştir**

  Yerel makinede kaynak kodu olmadığında veya *. pdb* dosyası kaynak kodla eşleşmezse, bir uygulamada hata ayıklamaya yardımcı olması Için kaynak sunucuyu kullanır. Kaynak sunucu, dosya isteklerini alır ve kaynak denetiminden gerçek dosyaları döndürür. Kaynak sunucu, uygulamanın *. pdb* dosyasını okumak için *srcsrv.dll* adlı bir dll kullanarak çalışır. *. Pdb* dosyası kaynak kodu deposuna yönelik işaretçiler ve kaynak kodu depodan almak için kullanılan komutları içerir.

  *srcsrv.dll* *srcsrv.ini* adlı bir dosyada izin verilen komutları listeleyerek, uygulamanın *. pdb* dosyasından yürütebilmesi gereken komutları sınırlayabilirsiniz. *srcsrv.ini* dosyasını *srcsrv.dll* ve *devenv.exe* aynı klasöre yerleştirin.

  >[!IMPORTANT]
  >Rastgele komutlar uygulamanın *. pdb* dosyasına katıştırılabildiğinden, yalnızca yürütmek istediğiniz komutları bir *srcsrv.ini* dosyasına yerleştirdiğinizden emin olun. *srcsvr.ini* dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için bkz. [güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, *srcsrv.ini* *cmd.exe* listeleniyorsa, kötü niyetli bir Kullanıcı *cmd.exe* , tehlikeli hale getirmek için parametreler belirtebilir.

  Bu öğeyi ve istediğiniz alt öğeleri seçin. **Kısmi güven derlemeleri (yalnızca yönetilen) için kaynak sunucuya Izin ver** ve **hiçbir zaman güvenilmeyen kaynak sunucu komutlarını sormadan Çalıştır** güvenlik risklerini artırabilir.

  ![Kaynak sunucu seçeneklerini etkinleştirme](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Derleyici simgesi seçenekleri

Standart Hata Ayıklama derleme yapılandırmasıyla Visual Studio IDE'den bir proje derlemeniz, C++ ve yönetilen derleyiciler kodunuz için uygun sembol dosyalarını oluşturmanızı sağlar.  Kodda derleyici seçeneklerini de ayarlayabilirsiniz.

### <a name="net-options"></a>.NET seçenekleri

.pdb dosyası oluşturmak için **/debug** *ile derleme.* **/debug:full veya** **/debug:pdbonly ile uygulama derlemek için.** **/debug:full ile oluşturma,** hata ayıklanabilir kod üretir. **/debug:pdbonly** ile derlenmesi *.pdb* dosyaları üretir, ancak JIT derleyiciye hata ayıklama bilgisinin kullanılabilir olduğunu söyleyen `DebuggableAttribute` dosyası oluşturmaz. Hata ayıklanabilir olmak istemeyebilirsiniz bir yayın derlemesi *için .pdb* dosyaları oluşturmak için **/debug:pdbonly** kullanın. Daha fazla bilgi için bkz. [/debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) veya [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>C/C++ seçenekleri

- *VC \<x> .pdb* ve *\<project> .pdb* dosyaları

  /ZI veya /Zi ile derleme oluşturulduğunda C/C++ için bir *.pdb* [dosyası oluşturulur.](/cpp/build/reference/z7-zi-zi-debug-information-format) içinde [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] [, /Fd seçeneği](/cpp/build/reference/fd-program-database-file-name) derleyicinin oluşturduğu *.pdb* dosyasını olarak adlar. IDE kullanarak içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir proje sanız, **/Fd** seçeneği *\<project> .pdb* adlı bir *.pdb* dosyası oluşturmak için ayarlanır.

  Derleme dosyası kullanarak C/C++ uygulamanızı derler ve **/Fd** kullanmadan **/ZI** veya **/Zi** belirtirsiniz, derleyici iki *.pdb dosyası* oluşturur:

  - *VC \<x> .pdb*, burada Microsoft C++ derleyici sürümünü *\<x>* temsil eder, örneğin *VC11.pdb*

    *VC \<x> .pdb dosyası,* tek tek nesne dosyaları için tüm hata ayıklama bilgilerini depolar ve proje oluşturma dosyasıyla aynı dizinde bulunur. Bir nesne dosyası oluşturduğu her zaman C/C++ derleyicisi, hata ayıklama bilgilerini *VC \<x> .pdb'de birler.* Bu nedenle, her kaynak dosya gibi ortak üst bilgi dosyaları içerirse bile, bu üst bilgilerden tür tanımları her nesne dosyasında değil *\<windows.h>* yalnızca bir kez depolanır. Eklenen bilgiler tür bilgilerini içerir ancak işlev tanımları gibi sembol bilgilerini içermez.

  - *\<project>Pdb*

    *\<project> .pdb* dosyası, projenin.exetüm hata  ayıklama bilgilerini depolar ve *\debug alt* dizininde yer almaktadır. *\<project> .pdb dosyası,* *yalnızca VC \<x> .pdb* içinde bulunan tür bilgilerini değil işlev prototipleri de dahil olmak üzere tam hata ayıklama bilgilerini içerir.

  VC *\<x> .pdb ve .pdb* *\<project> dosyaları artımlı güncelleştirmelere* izin sağlar. Ayrıca, bağlantıcı *.pdb* dosyalarının yolunu.exe *veya oluşturduğu.dll* dosyasına da katıştırır.

- <a name="use-dumpbin-exports"></a>DLL dışarı aktarma tabloları

  `dumpbin /exports`Dll'nin dışarı aktarma tablosunda bulunan sembolleri görmek için kullanın. DLL dışarı aktarma tablolarından sembolik bilgiler, Windows iletileri, Windows yordamları (WindowProcs), COM nesneleri, sıralama veya sembole sahip olmadığınız DLL'lerle çalışmak için yararlı olabilir. Semboller tüm 32-bit sistem DLL için kullanılabilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir.

  Çıkışı `dumpbin /exports` okuyarak alfasayısal olmayan karakterler de dahil olmak üzere işlev adlarının tam olarak nasıl olduğunu görebilir. İşlev adlarının hata ayıklayıcıda başka bir yerde kesilebilir olması nedeniyle işlev adlarını tam olarak görmek işlevde kesme noktası ayarlama açısından yararlıdır. Daha fazla bilgi için bkz. [dumpbin /exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Web uygulamaları

Uygulama *web.config* hata ayıklama ASP.NET dosyasını ayarlayın. Hata ayıklama modu ASP.NET'in dinamik olarak oluşturulan dosyalar için sembol oluşturmasına neden olur ve hata ayıklayıcının ASP.NET uygulamasına eklemesine olanak tanır. Visual Studio, projenizi web projeleri şablonundan oluşturduysanız hata ayıklamaya başsanız bunu otomatik olarak ayarlar.

## <a name="manage-symbols-while-debugging"></a>Hata ayıklama sırasında sembolleri yönetme

Hata ayıklama sırasında sembolleri  **yüklemek veya** sembol seçeneklerini değiştirmek  için Modüller, Çağrı **Yığını,** YerelLer, Otomatikler veya herhangi bir İzleme penceresini kullanabilirsiniz. Daha fazla bilgi için [bkz. Hata ayıklayıcının uygulamanıza nasıl ekli olduğu hakkında daha fazla bilgi.](../debugger/debugger-tips-and-tricks.md#modules_window)

### <a name="work-with-symbols-in-the-modules-window"></a>Modüller penceresinde sembollerle çalışma

Hata ayıklama sırasında **Modüller penceresi,** hata ayıklayıcının kullanıcı kodu veya Kodum olarak davranarak kod modüllerini ve sembol yükleme durumunu gösterir. Ayrıca Modüller penceresinde sembol yükleme durumunu, yük sembollerini ve sembol seçeneklerini **değiştirebilirsiniz.**

**Hata ayıklama sırasında sembol konumlarını veya seçeneklerini izlemek veya değiştirmek için:**

1. Modüller penceresini **açmak için** hata ayıklama sırasında Modüllerde Hata Ayıkla'Windows  >    >   seçin (veya **Ctrl** Alt U  +  **tuşlarına**  +  **basın).**
1. Modüller **penceresinde** Sembol Durumu veya Sembol Dosyası **üst bilgilerine** **veya** herhangi bir modüle sağ tıklayın.
1. Bağlam menüsünde aşağıdaki seçeneklerden birini belirleyin:

|Seçenek|Açıklama|
|------------|-----------------|
|**Sembolleri Yükleme**|Atlanmış, bulunamayan veya yüklenmemiş sembollere sahip modüller için görünür. Seçenekler Hata Ayıklama Sembolleri sayfasında belirtilen **konumlardan**  >  **sembolleri yükleme**  >  **denemeleri.** Sembol dosyası bulunamıyor veya yüklenmemişse, arama **yapmak Dosya Gezgini** için yeni bir konum belirtebilirsiniz.|
|**Sembol Yükleme Bilgisi**|Yüklenen sembol dosyasının konumunu veya hata ayıklayıcı dosyayı bulamıyorsa aranan konumları gösterir.|
|**Sembol Ayarlar**|Sembol   >  **konumlarını**  >  **düzenleyemez ve** ekleyemezsiniz, Seçenekler Hata Ayıklama Sembolleri sayfasını açar.|
|**Her Zaman Otomatik Olarak Yükle**|Seçilen sembol dosyasını hata ayıklayıcı tarafından otomatik olarak yüklenen dosyalar listesine ekler.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Simge Yüklenmedi/Kaynak Yüklenmedi sayfalarını kullanın

Hata ayıklayıcının sembol veya kaynak dosyaları mevcut değil koda girebilirsiniz:

- Koda adımla.
- Kesme noktası veya özel durum koduna girin.
- Farklı bir iş parçacığına geçiş.
- Çağrı Yığını penceresinde bir kareye çift tıklayarak yığın **çerçevesini** değiştirme.

Bu durumda, hata ayıklayıcı gerekli sembolleri  veya kaynağı bulup **yüklemeye** yardımcı olmak için Simge Yüklenmedi veya Kaynak Yüklenmedi sayfalarını görüntüler.

 ![Simge Yüklenmedi sayfası](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Eksik sembolleri bulmaya ve yüklemeye yardımcı olmak için Simge Yüklenmedi belge sayfasını kullanmak için:**

- Arama yolunu değiştirmek için, seçilmemiş bir yol  seçin veya Yeni Yol veya Yeni **VSTS Yolu'seçin** ve yeni bir yol girin veya seçin. Yolları **yeniden** aramak ve bulunursa sembol dosyasını yüklemek için Yükle'yi seçin.
- Sembol seçeneklerini geçersiz kılmak ve arama yollarını yeniden denemek için Gözat'ı seçin **ve öğesini bulun. \<executable-name>** Sembol dosyası bulunursa yüklenir veya **Dosya Gezgini,** böylece sembol dosyasını el ile seçebilirsiniz.
- Davranışı yapılandırmak üzere sembol ayarları sayfasını açmak için Sembol Ayarlarını  **Değiştir'i Ayarlar (veya** Seçenekler Hata Ayıklama  >  **Sembolleri) seçeneğini**  >  **belirleyin.**
- (Gelişmiş) Ayrımları yeni bir pencerede bir kez göstermek için, kaynağın veya  sembol dosyalarının bulunamamaysa da her zaman **deassembly'yi** gösterecek şekilde ayarlamak için, ayrımları görüntüle seçeneğini belirleyin veya Seçenekler iletişim kutusunu seçin. Daha fazla bilgi için [bkz. Farklı kodu görüntüleme.](../debugger/how-to-use-the-disassembly-window.md)
- Aranan konumları ve sonucu göstermek için Sembol yükleme **bilgileri'ne tıklayın.**
- C# kodu için, Kaynak [](../debugger/decompilation.md) kodun kaynak kodunu Yüklenmemiş Sembol Yok veya Kaynak Yüklenmedi **sayfalarından da kaynak kodun kodunun nasıl kaynak koda kod olarak kaynak koda kod olarak koda kod olarak yüklenemiyor olduğunu seçebilirsiniz.** 

Hata ayıklayıcısı seçeneklerden birini yürüttkten sonra *.pdb* dosyasını bulursa ve *.pdb* dosyasındaki bilgileri kullanarak kaynak dosyayı alabilirse, kaynağı görüntüler. Aksi takdirde, sorunu **çözecek eylemlerin** bağlantılarıyla birlikte sorunu açıklayan Bir Kaynak Yüklenmedi sayfası görüntülenir.

**Bir çözüme kaynak dosya arama yolları eklemek için:**

Hata ayıklayıcının kaynak dosyaları arayıcı tarafından aranacak konumları belirtebilirsiniz ve belirli dosyaları aramanın dışında tutabilirsiniz.

1. içinde çözümü seçin **Çözüm Gezgini** simgesini seçin,  **Alt** Enter tuşuna basın veya sağ + tıklar ve Özellikler'i **seçin.**

1. Kaynak **Dosyalarda Hata Ayıkla'ya seçin.**

   ![Kaynak dosyalarında hata ayıklama sayfası](../debugger/media/dbg-source-files.png)

1. Kaynak **kodunu içeren dizinler'in** altına arama yapmak için kaynak kodu konumlarını yazın veya seçin. Daha fazla konum **eklemek** için Yeni  Satır  simgesini, yeniden sıralamak için Yukarı ve Aşağı ok simgelerini veya **silmek için X** simgesini kullanın.

   >[!NOTE]
   >Hata ayıklayıcısı yalnızca belirtilen dizinde arama sağlar. Arama yapmak istediğiniz alt dizinler için girdi eklemeniz gerekir.

1. Bu **kaynak dosyaları arama altında,** aramanın dışında tutulacak kaynak dosyaların adlarını yazın.

1. **Tamam'ı veya** Uygula'yi **seçin.**

## <a name="see-also"></a>Ayrıca bkz.
- [Sembol dosyalarını ve Visual Studio ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [2012 ve 2013 Visual Studio .NET uzak sembol yükleme değişiklikleri](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
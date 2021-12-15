---
title: Hata ayıklayıcıda sembol (. pdb) ve kaynak dosyaları ayarlama
description: Visual Studio sembol ve kaynak dosyalarını yapılandırma ve yönetme hakkında bilgi edinin
ms.date: 12/09/2021
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
ms.openlocfilehash: a7e6694eeb17f67fff12a00d5e3627b6fb8d9fb1
ms.sourcegitcommit: dc392e126dbd9176825fe68cfc10ede121cde0bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2021
ms.locfileid: "135047886"
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

     ::: moniker range=">= vs-2022"
     ![Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası](media/vs-2022/dbg-options-symbols.png "Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası")
     ::: moniker-end
     ::: moniker range="<= vs-2019"
     ![Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası](media/dbg-options-symbols.gif "Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası")
     ::: moniker-end

     >[!NOTE]
     >Yalnızca belirtilen klasör aranır. Aramak istediğiniz alt klasörler için girdi eklemeniz gerekir.

   - Yeni bir VSTS sembol sunucusu konumu eklemek için
     1. Araç çubuğundaki ![araçlar&#47; seçenekler&#47; hata ayıklama&#47;simgeler yeni sunucu simgesi](media/dbg_tools_options_foldersicon.png "Araçlar &#45; seçenekler &#45; hata ayıklama &#45; simgeler yeni sunucu simgesi") simgesini seçin.
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

  ![Seçenekler &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri](../debugger/media/dbg-options-general-disassembly-checkbox.png "Seçenekler &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Kaynak sunucu desteğini etkinleştir**

  Yerel makinede kaynak kodu olmadığında veya *. pdb* dosyası kaynak kodla eşleşmezse, bir uygulamada hata ayıklamaya yardımcı olması Için kaynak sunucuyu kullanır. Kaynak sunucu, dosya isteklerini alır ve kaynak denetiminden gerçek dosyaları döndürür. Kaynak sunucu, uygulamanın *. pdb* dosyasını okumak için *srcsrv.dll* adlı bir dll kullanarak çalışır. *. Pdb* dosyası kaynak kodu deposuna yönelik işaretçiler ve kaynak kodu depodan almak için kullanılan komutları içerir.

  *srcsrv.dll* *srcsrv.ini* adlı bir dosyada izin verilen komutları listeleyerek, uygulamanın *. pdb* dosyasından yürütebilmesi gereken komutları sınırlayabilirsiniz. *srcsrv.ini* dosyasını *srcsrv.dll* ve *devenv.exe* aynı klasöre yerleştirin.

  >[!IMPORTANT]
  >Rastgele komutlar uygulamanın *. pdb* dosyasına katıştırılabildiğinden, yalnızca yürütmek istediğiniz komutları bir *srcsrv.ini* dosyasına yerleştirdiğinizden emin olun. *srcsvr.ini* dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için bkz. [güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, *srcsrv.ini* *cmd.exe* listeleniyorsa, kötü niyetli bir Kullanıcı *cmd.exe* , tehlikeli hale getirmek için parametreler belirtebilir.

  Bu öğeyi ve istediğiniz alt öğeleri seçin. **Kısmi güven derlemeleri (yalnızca yönetilen) için kaynak sunucuya Izin ver** ve **hiçbir zaman güvenilmeyen kaynak sunucu komutlarını sormadan Çalıştır** güvenlik risklerini artırabilir.

  ![Kaynak sunucu seçeneklerini etkinleştir](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Derleyici sembol seçenekleri

standart **hata ayıklama** yapı yapılandırmasıyla Visual Studio ıde 'den bir proje oluşturduğunuzda, C++ ve yönetilen derleyiciler kodunuz için uygun sembol dosyalarını oluşturur. Ayrıca, koddaki derleyici seçeneklerini de ayarlayabilirsiniz.

### <a name="net-options"></a>.NET seçenekleri

Bir *. pdb* dosyası oluşturmak için **/Debug** ile derleyin. **/Debug: Full** veya **/Debug: pdbonly** ile uygulamalar oluşturabilirsiniz. **/Debug: Full** ile derleme hata ayıklanabilir kodu oluşturur. **/Debug: pdbwıth** ile derleme yalnızca *. pdb* dosyaları oluşturur, ancak `DebuggableAttribute` JIT derleyicisine hata ayıklama bilgilerinin kullanılabildiğini söyleyen öğesini oluşturmaz. Hata ayıklanabilir olmasını istemediğiniz bir yayın derlemesi için *. pdb* dosyaları oluşturmak istiyorsanız **/Debug: pdbonly** kullanın. Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) veya [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>C/C++ seçenekleri

- *VC \<x> . pdb* ve *\<project> . pdb* dosyaları

  C/C++ için bir *. pdb* dosyası [/Zi veya/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)ile derleme yaptığınızda oluşturulur. [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]' De, [/FD](/cpp/build/reference/fd-program-database-file-name) seçeneği derleyicinin oluşturduğu *. pdb* dosyasını adlandırır. IDE 'yi kullanarak ' de bir proje oluşturduğunuzda [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , **/FD** seçeneği *\<project> . pdb* adlı bir *. pdb* dosyası oluşturmak üzere ayarlanır.

  C/C++ uygulamanızı bir Makefile kullanarak derleyebilir ve **/zı** ya da **/Zi** 'yi **/FD** kullanmadan belirtirseniz, derleyici iki *. pdb* dosyası oluşturur:

  - *VC \<x> . pdb*, *\<x>* Microsoft C++ derleyicisinin sürümünü temsil eder, örneğin *VC11. pdb*

    *VC \<x> . pdb* dosyası, bireysel nesne dosyaları için tüm hata ayıklama bilgilerini depolar ve proje derleme görevleri dosyası ile aynı dizinde bulunur. Bir nesne dosyası her oluşturduğunda, C/C++ derleyicisi hata ayıklama bilgilerini *VC \<x> . pdb* ile birleştirir. Her kaynak dosya gibi ortak üst bilgi dosyalarını içerse de *\<windows.h>* , bu başlıklardan tür tanımları her nesne dosyası yerine yalnızca bir kez depolanır. Ekli bilgiler tür bilgilerini içerir, ancak işlev tanımları gibi sembol bilgilerini içermez.

  - *\<project>. pdb*

    *\<project> . Pdb* dosyası, projenin *.exe* dosyası için tüm hata ayıklama bilgilerini depolar ve *ta \debug* alt dizininde bulunur. *\<project> . Pdb* dosyası, yalnızca *VC \<x> . pdb*'de bulunan tür bilgilerini değil, işlev prototipleri dahil olmak üzere tam hata ayıklama bilgileri içerir.

  Hem *VC \<x> . pdb* hem de *\<project> . pdb* dosyaları artımlı güncelleştirmelere izin verir. Bağlayıcı Ayrıca *. pdb* dosyalarının yolunu oluşturduğu *.exe* veya *.dll* dosyasına katıştırır.

- <a name="use-dumpbin-exports"></a>DLL dışarı aktarma tabloları

  `dumpbin /exports`DLL 'nin dışarı aktarma tablosunda kullanılabilen sembolleri görmek için kullanın. DLL dışarı aktarma tablolarından sembolik bilgiler, Windows iletilerle, Windows yordamlarla (windowprocs), COM nesneleriyle, sıralamaya veya sembollerine sahip olmadığınız herhangi bir DLL ile çalışmak için yararlı olabilir. Semboller tüm 32-bit sistem DLL için kullanılabilir. Aramalar geçerli işlev en üstte (en yoğun şekilde iç içe geçmiş) olacak şekilde arama sırasıyla listelenir.

  Çıktıyı okuyarak, `dumpbin /exports` alfasayısal olmayan karakterler de dahil olmak üzere tam işlev adlarını görebilirsiniz. İşlev adlarının hata ayıklayıcıdaki başka bir yerde kesilebilir olduğu için işlev adlarının tam olarak ayarlanması, bir işlevde kesme noktası ayarlamak için yararlıdır. Daha fazla bilgi için bkz. [dumpbin/dışarı aktarmalar](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Web uygulamaları

ASP.NET uygulamanızın *web.config* dosyasını hata ayıklama moduna ayarlayın. Hata ayıklama modu ASP.NET'in dinamik olarak oluşturulan dosyalar için sembol oluşturmasına neden olur ve hata ayıklayıcının ASP.NET uygulamasına eklemesine olanak tanır. Visual Studio, projenizi web projeleri şablonundan oluşturduysanız, hata ayıklamaya başladığınızda bu otomatik olarak ayarlar.

## <a name="manage-symbols-while-debugging"></a>Hata ayıklama sırasında sembolleri yönetme

Hata ayıklama sırasında sembolleri yüklemek veya sembol seçeneklerini değiştirmek için **modüller**, **çağrı yığını**, **Yereller**, **oto** veya herhangi bir **Gözcü** penceresi kullanabilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcının uygulamanıza nasıl ilişi hakkında daha fazla bilgi edinin](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Modüller penceresinde semboller ile çalışma

Hata ayıklama sırasında **modüller** penceresi, hata ayıklayıcının Kullanıcı kodu veya kodum olarak davranılması ve sembol yükleme durumu olarak davranması için kod modüllerini gösterir. Ayrıca, **modüller** penceresindeki sembol yükleme durumunu izleyebilir, sembolleri yükleyebilir ve sembol seçeneklerini değiştirebilirsiniz.

**Hata ayıklarken sembol konumlarını veya seçeneklerini izlemek veya değiştirmek için:**

1. **modüller** penceresini açmak için **hata ayıklama sırasında**  >  **Windows**  >  **modüller** ' i (veya **Ctrl**  +  **Alt**  +  **U** tuşlarına basın) seçin.
1. **Modüller** penceresinde, **sembol durumu** veya **sembol dosyası** üst bilgilerine veya herhangi bir modüle sağ tıklayın.
1. Bağlam menüsünde, aşağıdaki seçeneklerden birini seçin:

|Seçenek|Açıklama|
|------------|-----------------|
|**Sembolleri yükle**|Atlanan, bulunmayan veya yüklü sembolleri olmayan modüller için görüntülenir. **Seçenekler**  >  **hata ayıklama**  >  **sembolleri** sayfasında belirtilen konumlardan sembolleri yüklemeye çalışır. Sembol dosyası bulunamazsa veya yüklü değilse, arama için yeni bir konum belirleyebilmeniz için **dosya gezginini** başlatır.|
|**Sembol Yükleme Bilgisi**|Yüklü bir sembol dosyasının konumunu veya hata ayıklayıcı dosyayı bulamazsa aranan konumları gösterir.|
|**sembol Ayarlar**|  >    >  Sembol konumlarını düzenleyebileceğiniz ve ekleyebileceğiniz seçenekler hata ayıklama **sembolleri** sayfasını açar.|
|**Her zaman otomatik olarak yükle**|Seçilen sembol dosyasını, hata ayıklayıcı tarafından otomatik olarak yüklenen dosyalar listesine ekler.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Yüklü simge yok/kaynak yüklenmedi sayfası kullan

Hata ayıklayıcının sembol veya kaynak dosyalarına sahip olmayan kodu bozmak için çeşitli yollar vardır:

- Koda adımla.
- Bir kesme noktasından veya özel durumdan koda bölün.
- Farklı bir iş parçacığına geçiş yapın.
- **Çağrı yığını** penceresinde bir çerçeveyi çift tıklayarak yığın çerçevesini değiştirin.

Bu durumda, hata ayıklayıcı **yüklü sembol yok** veya gerekli sembolleri veya kaynağı bulmanıza ve yüklemeye yardımcı olacak **hiçbir kaynak yüklenmedi** sayfası görüntüler.

 ![Simge yüklenmedi sayfası yok](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Eksik sembolleri bulmaya ve yüklemeye yardımcı olması için simge yüklenmemiş belge sayfasını kullanmak için:**

- Arama yolunu değiştirmek için, seçilmemiş bir yolu seçin veya **yeni yol** veya **Yeni VSTS yolu** ' nu seçin ve yeni bir yol girin veya seçin. Yolları tekrar aramak ve bulunursa sembol dosyasını yüklemek için **Yükle** ' yi seçin.
- Herhangi bir sembol seçeneklerini geçersiz kılmak ve arama yollarını yeniden denemek için, **Araştır ve \<executable-name> bul**' u seçin. Sembol dosyası bulunursa yüklenir veya sembol dosyasını el ile seçebilmeniz için **Dosya Gezgini** açılır.
- davranışı yapılandırmak üzere sembol ayarları sayfasını açmak için **sembol Ayarlar değiştir** ' i seçin (veya **seçenekleri**  >  **hata ayıklama**  >  **sembolleri** seçin).
- Ileri Ayrıştırılmış derlemeyi bir kez yeni bir pencerede göstermek için, ayrıştırılmış **derlemeyi görüntüle**' yi seçin veya kaynak veya sembol dosyaları bulunamadığında her zaman ayrıştırılmış derlemeyi göster seçeneğini ayarlamak için **Seçenekler iletişim kutusunu** seçin. Daha fazla bilgi için bkz. [ayrıştırma kodunu görüntüleme](../debugger/how-to-use-the-disassembly-window.md).
- Aranan konumları ve sonucu göstermek için **sembol yükleme bilgileri**' ni genişletin.
- C# kodu için, kaynak kodu **yüklü olmayan** veya **kaynak yüklenmemiş** sayfalardan [derlemeyi kaldırma](../debugger/decompilation.md) seçeneğini de belirleyebilirsiniz.

Seçeneklerden birini yürütmeden sonra hata ayıklayıcı *. pdb* dosyasını bulursa ve *. pdb* dosyasındaki bilgileri kullanarak kaynak dosyayı alabiliyorsanız, kaynağı görüntüler. Aksi halde, sorunu giderebilecek eylemlerin bağlantılarıyla birlikte, sorunu açıklayan bir **kaynak yüklenmemiş** sayfa görüntüler.

**Bir çözüme kaynak dosya arama yolları eklemek için:**

Hata ayıklayıcının kaynak dosyalarını arayacağı konumları belirtebilir ve belirli dosyaları aramadan dışlayabilirsiniz.

1. **Çözüm Gezgini**' de çözümü seçin ve ardından **Özellikler** simgesini seçin, **alt** + **ENTER** tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **Kaynak dosyalarını hata ayıkla**' yı seçin.

   ![Kaynak dosyalarını hata ayıkla sayfası](../debugger/media/dbg-source-files.png)

1. **Kaynak kodu Içeren dizinler** altında, Aranacak kaynak kodu konumlarını yazın veya seçin. **Yeni satır** simgesini kullanarak daha fazla konum ekleyin, **yukarı** ve **aşağı** ok simgelerini yeniden sıralayın veya **X** simgesini silin.

   >[!NOTE]
   >Hata ayıklayıcı yalnızca belirtilen dizini arar. Arama yapmak istediğiniz alt dizinler için girdi eklemeniz gerekir.

1. **Bu kaynak dosyalara bakmayın** altında, aramadan dışlanacak kaynak dosyalarının adlarını yazın.

1. **Tamam ' ı** veya **Uygula**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [sembol dosyalarını ve Visual Studio sembol ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [.net uzak sembol Visual Studio 2012 ve 2013 değişikliklerini yükleme](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
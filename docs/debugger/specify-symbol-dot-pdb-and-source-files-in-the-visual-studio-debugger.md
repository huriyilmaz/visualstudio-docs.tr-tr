---
title: Hata ayıklayıcısında sembol (.pdb) ve kaynak dosyaları ayarlama
description: Kaynak dosyalarında sembol ve kaynak dosyaları yapılandırmayı ve yönetmeyi Visual Studio
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090414"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında (C#, C++, Visual Basic, F#) sembolünü (.pdb) ve kaynak dosyaları belirtin

Projenizin kaynak kodundaki sembol dosyaları, eşleme tanımlayıcıları ve deyimleri olarak da adlandırılan program veritabanı (*.pdb*) dosyaları, derlenmiş uygulamalarda karşılık gelen tanımlayıcılara ve yönergelere. Bu eşleme dosyaları, hata ayıklayıcıyı kaynak kodunuzla bağlantılandırarak hata ayıklamayı sağlar.

Standart Hata Ayıklama derleme yapılandırmasıyla Visual Studio IDE'den bir proje yapılandırmasını derlerken, derleyici uygun sembol dosyalarını oluşturur. Bu makalede IDE'de sembol dosyalarının nasıl yönet kuralları açıklanmıştır. Örneğin, hata ayıklayıcı seçeneklerinde simgelerin konumunu [belirtme,](#BKMK_Specify_symbol_locations_and_loading_behavior)hata ayıklama sırasında sembol yükleme durumunu denetleme ve kodda sembol seçeneklerini [](#work-with-symbols-in-the-modules-window) [ayarlama.](#compiler-symbol-options)

Sembol dosyalarının ayrıntılı açıklaması için aşağıdakilere bakın:

- [Sembol dosyalarını ve Visual Studio ayarlarını anlama](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Neden Visual Studio hata ayıklayıcısı sembol dosyalarının, kendileriyle derlenilen ikili dosyalarla tam olarak eşleşmesi gerekir?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Sembol dosyaları nasıl çalışır?

*.pdb dosyası,* hata ayıklama ve proje durumu bilgilerini tutar. Bu bilgiler, uygulamanın Hata Ayıklama yapılandırmasının artımlı olarak bağlantı oluşturmasını sağlar. Hata Visual Studio hata ayıklayıcısı hata ayıklarken iki önemli bilgi parçası belirlemek için *.pdb* dosyalarını kullanır:

* Kaynak dosya adı ve IDE'de Visual Studio numarası.
* Kesme noktası için uygulamanın nerede duracak?

Sembol dosyaları ayrıca kaynak dosyaların konumunu ve isteğe bağlı olarak bunları almak için sunucuyu gösterir.

Hata ayıklayıcı yalnızca bir uygulama oluşturulduğunda (yani özgün .pdb dosyaları veya kopyaları) *oluşturulan .pdb* dosyalarıyla tam olarak eşan.pdb dosyalarını yükler.   Bu [tam yineleme](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) gereklidir çünkü kodun kendisi değişmese bile uygulamaların düzeni değişebilir.

> [!TIP]
> Proje çağrılarınızı Windows kodu veya üçüncü taraf kod gibi proje kaynak kodunuzun dışında kodda hata ayıklamak için, dış kodun *.pdb* dosyalarının (ve isteğe bağlı olarak kaynak dosyalarının) konumunu belirtmeniz gerekir. Bu, uygulama derlemeleri ile tam olarak eşleşmesi gerekir.

## <a name="symbol-file-locations-and-loading-behavior"></a>Sembol dosyası konumları ve yükleme davranışı

IDE'de bir projenin Visual Studio ayıklarken, hata ayıklayıcı proje klasöründe bulunan sembol dosyalarını otomatik olarak yükler.

> [!NOTE]
> Uzak bir cihazda yönetilen kodda hata ayıklarken, tüm sembol dosyalarının yerel makinede veya hata ayıklayıcı seçeneklerinde belirtilen bir [konumda yer alıyor olması gerekir.](#BKMK_Specify_symbol_locations_and_loading_behavior)

Hata ayıklayıcısı ayrıca aşağıdaki konumlarda sembol dosyalarını arar:

1. DLL veya yürütülebilir *dosya*(.exe) içinde belirtilen konum.

   Varsayılan olarak, bilgisayarınızda bir DLL veya *.exe* dosyası bilgisayarınızda varsa, bağlantıcı dll veya dosya dosyasına ilişkili *.pdb* dosyasının tam yolunu ve *dosya adını.exe.* Hata ayıklayıcısı, sembol dosyasının o konumda var olup olduğunu denetler.

2. DLL veya dosyayla aynı *.exe.*

3. Sembol dosyaları için hata ayıklayıcı seçeneklerinde belirtilen herhangi bir konum. Sembol konumlarını eklemek ve etkinleştirmek için [bkz. Sembol konumlarını yapılandırma ve yükleme seçenekleri.](#BKMK_Specify_symbol_locations_and_loading_behavior)

   - Herhangi bir yerel sembol önbellek klasörü.

   - Seçiliyse Microsoft Sembol Sunucuları gibi belirtilen ağ, internet veya yerel sembol sunucuları ve konumları. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , protokolü uygulayan sembol sunucularından hata ayıklama sembol dosyalarını `symsrv` indirebilir. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) ve Hata [Ayıklama Araçları Windows](/windows-hardware/drivers/debugger/index) sembol sunucularını kullana iki araçtır.

     Kullanabileceğiniz sembol sunucuları şunlardır:

     **Genel Microsoft Sembol Sunucuları:** Bir sistem DLL'sini veya üçüncü taraf kitaplığını çağırma sırasında oluşan bir kilitlenmede hata ayıklamak için genellikle sistem *.pdb* dosyaları gerekir. Sistem *.pdb* dosyaları, Windows,.exeve *cihaz* sürücüleri için semboller içerir. Genel Microsoft Sembol Sunucularından Windows sistemleri, MDAC, IIS, ISA ve .NET için semboller edinebilirsiniz.

     **Bir iç ağ veya yerel** makineniz üzerinde sembol sunucuları: Takımınız veya şirketiniz, kendi ürünleriniz için sembol sunucuları ve dış kaynaklardan gelen semboller için bir önbellek olarak oluşturabilir. Kendi makineniz üzerinde bir sembol sunucusu olabilir.

     **Üçüncü taraf sembol sunucuları:** Uygulama ve kitaplıkların Windows üçüncü taraf sağlayıcıları, internet üzerinde sembol sunucusuna erişim sağlar.

     > [!WARNING]
     > Genel Microsoft Sembol Sunucuları dışında bir sembol sunucusu kullanıyorsanız, sembol sunucusunun ve yolunun güvenilir olduğundan emin olun. Sembol dosyaları rastgele yürütülebilir kod içerene kadar güvenlik tehditlerine maruz kalmış olabilir.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Sembol konumlarını ve yükleme seçeneklerini yapılandırma

Araçlar **Seçenekleri**  >  **Hata**  >  **Ayıklama Sembolleri**  >  **sayfasında** şunları yapabilirsiniz:

- Microsoft, Windows veya üçüncü taraf bileşenleri için arama yollarını ve sembol sunucularını belirtin ve seçin.
- Hata ayıklayıcının sembolleri otomatik olarak yüklemesi için istediğiniz veya olmadığınız modülleri belirtin.
- Etkin olarak hata ayıklarken bu ayarları değiştirin. Bkz. [Hata ayıklama sırasında sembolleri yönetme.](#manage-symbols-while-debugging)

**Sembol konumlarını ve yükleme seçeneklerini belirtmek için:**

1. Bu Visual Studio Araçlar Seçenekleri **Hata Ayıklama** Sembolleri (veya Hata Ayıklama Seçenekleri  >    >    >     >  **Sembolleri)**  >  **'i açın.**

2. Sembol **dosyası (.pdb) konumları altında,**
   - Microsoft Sembol **Sunucularını veya** **NuGet.org Sembol Sunucusunu kullanmak** için onay kutusunu işaretleyin.

   - Yeni bir sembol sunucusu konumu eklemek için,
     1. Araç **+** çubuğunda simgesini seçin.
     1. Metin alanına sembol sunucusunun URL'sini (http), ağ paylaşımını veya simge konumunun yerel yolunu yazın. Deyimi tamamlama doğru biçimi bulmanıza yardımcı olur.

     ![Tools &#45; Options &#45; Debugging &#45; Symbols sayfası](media/dbg-options-symbols.gif "Araçlar &#45; seçenekler &#45; hata ayıklama &#45; semboller sayfası")

     >[!NOTE]
     >Yalnızca belirtilen klasör aranır. Aramak istediğiniz alt klasörler için girdiler eklemeniz gerekir.

   - Yeni bir VSTS Sembol Sunucusu konumu eklemek için,
     1. Araç ![çubuğundaKimlik&#47; Seçenekler&#47;'&#47;Simgeler yeni sunucu](media/dbg_tools_options_foldersicon.png "Araçlar &#45; seçenekler &#45; hata ayıklama &#45; simgeler yeni sunucu simgesi") simgesi simgesini seçin.
     1. **VSTS Bağlan Sunucusuna** Ekle iletişim kutusunda, kullanılabilir sembol sunucularından birini seçin ve sonra da **Bağlan.**

   - Sembol konumlarını yükleme sıralarını değiştirmek için **Ctrl** Yukarı ve Ctrl Down tuşlarını veya Yukarı ve +   +  **Aşağı ok** **simgelerini** kullanın.
   - Url veya yolu düzenlemek için girişe çift tıklayın veya seçin ve **F2 tuşuna basın.**
   - Bir girişi kaldırmak için girdiyi seçin ve simgeyi **-** seçin.

3. (İsteğe bağlı) Sembol yükleme performansını artırmak için, **bu dizindeki Önbellek sembolleri'nin** altında, sembol sunucularının sembolleri kopyalayıp kopyalay siline bir yerel klasör yolu yazın.

   > [!NOTE]
   > Yerel sembol önbelleğini C:\Windows veya bir alt klasör gibi korumalı bir klasöre bağlayabilirsiniz. Bunun yerine okuma-yazma klasörü kullanın.

   > [!NOTE]
   > C++ projeleri için, ortam değişkeni ayarlanmışsa, bu dizinde Önbellek sembolleri `_NT_SYMBOL_PATH` altında ayarlanmış değeri geçersiz **kılar.**

4. Hata ayıklayıcının Sembol dosyası **(.pdb)** konumlarından başlatıldığında yüklemesi istediğiniz modülleri belirtin.

   - Hariç **tutulmadıkça** (varsayılan) Tüm modülleri yükle'yi seçerek sembol dosyası konumu içinde tüm modüllerin tüm sembollerini (özellikle hariç tutmak istediğiniz modüller hariç) yükle seçeneğini kullanın. Belirli modülleri hariç tutmak için Hariç **tutulacak** modülleri belirtin'i seçin, simgesini seçin, dışlanan modüllerin adlarını yazın **+** ve Tamam'ı **seçin.**

   - Sembol dosyası konumlarından yalnızca belirttiğiniz modülleri yüklemek için Yalnızca belirtilen modülleri **yükle'yi seçin.** Dahil **edilen modülleri belirtin'i** seçin, simgesini seçin, dahil edilecek modüllerin adlarını yazın ve **+** tamam'ı **seçin.** Diğer modüllerin sembol dosyaları yüklenmez.

5. **Tamam**’ı seçin.

## <a name="other-symbol-options-for-debugging"></a>Hata ayıklama için diğer sembol seçenekleri

Araçlar Seçenekler Hata Ayıklama Genel **(veya Hata**  >  **Ayıklama Seçenekleri**  >    >  **Genel)** içinde **ek sembol** seçenekleri  >    >  **seçebilirsiniz:**

- **Dll dışarı aktarmalarını yükleme (yalnızca yerel)**

  C/C++ için DLL dışarı aktarma tablolarını yükler. Ayrıntılar için bkz. [DLL dışarı aktarma tabloları.](#use-dumpbin-exports) DLL dışarı aktarma bilgilerini okumak biraz ek yük getirir, bu nedenle dışarı aktarma tablolarını yükleme varsayılan olarak kapalıdır. `dumpbin /exports`C/C++ derleme komut satırı da kullanabilirsiniz.

- **Adres düzeyinde hata ayıklamayı etkinleştirme** **ve Kaynak kullanılamıyorsa değerlendirmeyi göster**

  Kaynak veya sembol dosyaları bulunamadığnda her zaman disassembly gösterilir.

  ![Genel &#47; seçenekleri &#47; hata ayıklama seçenekleri](../debugger/media/dbg_options_general_disassembly_checkbox.png "Seçenekler &#47; hata ayıklama &#47; genel ayrıştırma seçenekleri")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Kaynak sunucu desteğini etkinleştirme**

  Yerel makinede kaynak kodu yoksa veya *.pdb* dosyası kaynak kodla eşleşmezse uygulamanın hata ayıklamasında yardımcı olması için Kaynak Sunucu'ya yardımcı olur. Kaynak Sunucu, dosyalar için istekleri alır ve kaynak denetiminden gerçek dosyaları döndürür. Kaynak Sunucu, uygulamanın *.pdb* *srcsrv.dll* içinsrcsrv.dlladlı bir DLL kullanarak çalışır. *.pdb* dosyası, kaynak kod deposuna işaretçilerin yanı sıra depodan kaynak kodu almak için kullanılan komutları içerir.

  izin verilen komutları srcsrv.dlladlı bir dosyada listeleerek uygulamanın *.pdb* dosyasından yürütebilirsiniz komutlarını *sınırsrcsrv.ini.* Dosya *srcsrv.ini* ile aynı klasöre *srcsrv.dll* ve *devenv.exe.*

  >[!IMPORTANT]
  >Rastgele komutlar bir uygulamanın *.pdb* dosyasına katıştırılanabizli olabilir, bu nedenle yalnızca yürütmek istediğiniz komutları bir uygulama *dosyasınasrcsrv.ini* olun. srcsvr.inidosyasında yer alan bir *komutu yürütme* girişimi bir onay iletişim kutusunun görünmesine neden olur. Daha fazla bilgi için [bkz. Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komutu Yürütmeli.](../debugger/security-warning-debugger-must-execute-untrusted-command.md)
  >
  >Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, *uygulamanızacmd.exe* *listelesrcsrv.ini* kötü amaçlı bir kullanıcı,cmd.exetehlikeli *hale* cmd.exeparametreleri belirterek.

  Bu öğeyi ve istediğiniz alt öğeleri seçin. **Kısmi güven derlemeleri için kaynak sunucuya izin ver (yalnızca yönetilen)** **ve** her zaman güvenilmeyen kaynak sunucu komutlarını istemi olmadan çalıştırmak güvenlik risklerini artırabilir.

  ![Kaynak sunucu seçeneklerini etkinleştir](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

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
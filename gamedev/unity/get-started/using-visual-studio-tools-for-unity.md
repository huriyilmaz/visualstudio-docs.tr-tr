---
title: Unity için Visual Studio Araçları | Microsoft Docs
description: Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı öğrenin. Unity geliştirmesi için Visual Studio hata ayıklayıcısını da kullanın.
ms.date: 12/10/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 157972a9f32ffe362c706b8eddaac923abaf47a2
ms.sourcegitcommit: 2a4744fb312396d36086dd59fd55ab741ae8e106
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "135575958"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde, Unity için Visual Studio Araçları'nin tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirmesi için Visual Studio hata ayıklayıcısını kullanmayı öğrenirsiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Unity betiklerini Visual Studio

Bu Visual Studio Unity için dış düzenleyici olarak ayarlanacaksa, [Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio)düzenleyicisinden bir betiği çift tıklamak otomatik olarak başlatılır veya Visual Studio ve seçilen betiği açar.

Alternatif olarak, Unity'de Visual Studio **C#** Aç menüsünü seçerek kaynak düzenleyicide açık betik > betik Project açabilirsiniz.

:::zone pivot="windows"
![C# projesini Visual Studio.](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![C# projesini Mac için Visual Studio.](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Unity belgelerine erişim

Unity betik belgelerine hızlı bir şekilde erişmek için Visual Studio. Api Unity için Visual Studio Araçları yerel olarak bulamazsanız, çevrimiçi bulmaya dener.

:::zone pivot="windows"
- Bu Visual Studio, imleci öğrenmek istediğiniz Unity API'sini vurgulayın veya üzerine yerleştirin, **ardından Ctrl** + **Alt** + **M**, **Ctrl** H tuşlarına + **basın**
- Ayrıca tuş bağlama yerine **> Unity API Başvurusu** menüsünü de kullanabilirsiniz.

![Visual Studio'da Unity API Başvurusu menüsünün ekran görüntüsü.](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Bu Mac için Visual Studio, imleci öğrenmek istediğiniz Unity API'sini vurgulayın veya üzerine yerleştirerek **Cmd'ye** + **basın**
- Ayrıca tuş bağlama yerine **> Unity API Başvurusu** menüsünü de kullanabilirsiniz.

![Mac için Visual Studio'de Unity API Başvurusu menüsünün ekran görüntüsü.](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>Unity API İletileri için IntelliSense

Intellisense kod tamamlama, MonoBehaviour betikleri içinde Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API'sini öğrenme konusunda yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. İmleci, sınıfından türeten bir sınıfın gövdesinin içindeki yeni bir satıra `MonoBehaviour` yerleştirebilirsiniz.

2. Gibi bir Unity iletinin adını yazmaya `OnTriggerEnter` başlayın.

3. **"ontri**" harfleri yazıldıktan sonra IntelliSense önerilerinin listesi görüntülenir.

:::zone pivot="windows"

![IntelliSense'i Visual Studio.](../media/vs/intellisense-example.png)  

:::zone-end

4. Liste seçimi üç şekilde değiştirilebilir:

    - Yukarı **ve Aşağı** **ok tuşlarıyla.**

    - fareyle istenen öğenin üzerine tıklayarak.

    - İstenen öğenin adını yazarak.

5. IntelliSense, gerekli parametreler de dahil olmak üzere seçili Unity iletiyi ekler:

    - Sekme tuşuna **basarak.**

    - Enter tuşuna **basarak.**

    - Seçilen öğeye çift tıklayarak.

:::zone pivot="windows"

![Visual Studio'de IntelliSense'den Unity ekle Visual Studio.](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior betik oluşturma sihirbazı

MonoBehavior sihirbazını kullanarak tüm Unity API yöntemlerinin listesini ekleyebilirsiniz ve hızlı bir şekilde boş bir tanım gerçekleştirebilirsiniz. Özellikle Yöntem açıklamalarını oluştur **seçeneği** etkinleştirildiğinde bu özellik, Unity API'sinde nelerin kullanılabilir olduğunu öğrenmeye devam ediyorsanız yararlıdır.

MonoBehavior sihirbazıyla boş MonoBehavior yöntem tanımları oluşturmak için:

1. Bu Visual Studio, imleci yöntemlerin eklenmesini istediğiniz konuma getirin ve **ardından** +  + MonoBehavior sihirbazını başlatmak için Ctrl Shift **M** tuşlarına basın. Bu Mac için Visual Studio **Cmd** Shift M +  + **tuşuna basın.**

2. Betik **yöntemleri oluştur penceresinde,** eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü **seçmek** için Framework sürümü açılan listesinden seçim yapmak.

4. Yöntemler varsayılan olarak imlecin bulunduğu konuma eklenir. Alternatif olarak, Ekleme noktası açılan listesinden değerini istediğiniz konuma değiştirerek bunları sınıfınıza  zaten uygulanmış herhangi bir yöntemden sonra eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemler için açıklama oluşturması için Yöntem açıklaması oluştur **onay kutusunu** işaretleyin. Bu açıklamalar, yöntemin ne zaman çağrıldısını ve genel sorumluluklarının ne olduğunu anlamanıza yardımcı olmak için amaçlıdır.

6. Sihirbazdan **çıkmak** ve yöntemleri kodunuza eklemek için Tamam düğmesini seçin.

:::zone pivot="windows"

![Visual Studio'da monobehavior sihirbazı iletişim kutusunun ekran görüntüsü.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![Mac için Visual Studio'da monobehavior sihirbazı iletişim kutusunun ekran Mac için Visual Studio.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Unity Project Gezgini
Unity Project Gezgini tüm Unity proje dosyalarınızı ve dizinlerinizi Unity Düzenleyicisi'nde olduğu gibi gösterir. Bu, Unity betiklerinizi projelerde ve Visual Studio Çözüm Gezgini oluşturulan bir çözümde düzenleyen normal komut dosyalarıyla gezinmekten Visual Studio.

:::zone pivot="windows"
- Ana menü Visual Studio Unity > **Gezgini'ni Project seçin.** Klavye kısayolu: **Alt** + **Shift** + **E**

![Unity Project Gezgini penceresinin ekran görüntüsü.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- Bu Mac için Visual Studio, Çözüm Bölmesi Unity projesi açıldığında otomatik olarak bu şekilde davranır.
:::zone-end
## <a name="unity-debugging"></a>Unity hata ayıklama

Unity için Visual Studio Araçları, Unity projenizin güçlü hata ayıklayıcısını kullanarak hem düzenleyici hem de Visual Studio betikleri hata ayıklamanıza olanak sağlar.

### <a name="debug-in-the-unity-editor"></a>Unity düzenleyicisinde hata ayıklama

#### <a name="start-debugging"></a>Hata ayıklamayı başlatma
:::zone pivot="windows"

1. Bağlan Visual Studio Unity'ye Ekle etiketli **Oynat** düğmesine tıklayarak **Unity'ye** tıklayın veya F5 klavye **kısayolunu kullanın.**

![Visual Studio'da Unity'ye Ekle düğmesinin ekran görüntüsü.](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. Bağlan Visual Studio Düğmesine tıklayarak **Unity'ye** tıklayın veya Komut **+ Dönüş veya** **F5 yazın.**

![Mac için Visual Studio'daki Oynat düğmesinin ekran görüntüsü.](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Unity'ye geçiş yapmak **ve oynat** düğmesine tıklayarak oyunu düzenleyicide çalıştırın.

:::zone pivot="windows"
![Windows'da Unity'de Oynat düğmesinin ekran görüntüsü.](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![macOS üzerinde Unity'de Oynat düğmesinin ekran görüntüsü.](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Oyun Visual Studio'a bağlıyken Unity düzenleyicisinde çalışırken, karşılaşılan tüm kesme noktaları oyunun yürütülmesini duraklatacak ve oyunun kesme noktasıyla karşılaştığı kod hattını Visual Studio.

#### <a name="stop-debugging"></a>Hata ayıklamayı durdurma

:::zone pivot="windows"

Visual Studio'da Durdur düğmesine tıklayın veya Shift + F5 klavye **kısayolunu kullanın.** 

![Visual Studio'daki Durdur düğmesinin ekran görüntüsü.](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Mac için Visual Studio'da Durdur düğmesine tıklayın veya **Shift + Komut + Return tuşlarına basın.** 

![Mac için Visual Studio'daki Durdur düğmesinin ekran görüntüsü.](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Uygulama içinde hata ayıklama hakkında daha fazla Visual Studio için bkz. Hata Ayıklayıcısı'nda hata [ayıklamaya Visual Studio belgeler.](/visualstudio/debugger/debugger-feature-tour).

#### <a name="attach-to-unity-and-play"></a>Unity ve Play'e ekleme

Daha fazla kolaylık sağlamak için Unity'ye **Ekle düğmesini Unity'ye** **Ekle ve Oynat moduna değiştirebilirsiniz.**

:::zone pivot="windows"

1. Unity'ye **Ekle düğmesinin** yanındaki **küçük aşağı oka** tıklayın.
2. Açılan **menüden Unity'ye Ekle** ve Oynat'ı seçin.

   ![Visual Studio'daki Ekle ve oynat düğmesinin ekran Visual Studio.](../media/vs/vstu-attach-and-play.png)

Oynat düğmesi Unity'ye Ekle **ve Oynat olarak etiketlenmiş olur.** Bu düğmeye tıklarsanız veya **F5** klavye kısayolunu kullanarak artık otomatik olarak Unity düzenleyicisine geçiş yapılır ve hata ayıklayıcının ek olarak oyun düzenleyicide Visual Studio çalışır.

:::zone-end
:::zone pivot="macos"
Unity'ye Ekle ve Oynat yapılandırması seçerek hata ayıklamayı başlatma ve Unity düzenleyicisini Mac için Visual Studio doğrudan tek bir adımda **tamamlanır.**

![Mac için Visual Studio'da Unity'ye Ekle ve Oynat düğmesinin ekran görüntüsü.](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> Unity'ye Ekle ve Oynat **yapılandırmasını kullanarak** hata ayıklamaya başladıysanız, Durdur **düğmesi** Unity Düzenleyicisi'ni de durdurur.

### <a name="debug-unity-player-builds"></a>Unity oynatıcı derlemeleri için hata ayıklama

Unity oyuncularının geliştirme derlemelerinin hata ayıklaması için Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity oynatıcıda betik hata ayıklamayı etkinleştirme

1. Unity'de Dosya ve Derleme Ayarlar'yi **seçerek Derleme >'Ayarlar.**
2. Derleme derlemesi Ayarlar Geliştirme **Derlemesi ve Betik Hata** **Ayıklama onay** kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarının ekran görüntüsü.](../media/vs/vstu-debugging-build-settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı eklemek için bir Unity örneği seçin

:::zone pivot="windows"

- Bu Visual Studio ana menüden Unity Hata Ayıklayıcısını **Ekle'> Ayıkla'ya tıklayın.**

   ![Visual Studio'da Unity Hata AyıklamaSı Ekleme Penceresinin ekran görüntüsü.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity Örneği Seç iletişim** kutusunda bağlanabilirsiniz her Unity örneği hakkında bazı bilgiler görüntülenir.

   ![Windows'da Bağlanmak için Unity örneği seçme penceresinin ekran Visual Studio.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Project** Unity'nin bu örneğinde çalışan Unity projesinin adı.

   **Makine** Unity'nin bu örneğinin üzerinde çalıştır olduğu bilgisayarın veya cihazın adı.

   **Türü** Unity'nin bu örneği Unity Düzenleyicisi'nin bir parçası olarak çalışıyorsa düzenleyici; Unity'nin bu örneği tek başına bir oyuncu ise oynatıcı.

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Unity için Visual Studio Araçları ve Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınız buna izin vermek için kural gerekebilir. Gerekirse, bir istem görebilirsiniz, bu durumda, VSTU ve Unity 'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.

#### <a name="selecting-a-unity-instance-that-doesnt-appear-in-the-list"></a>Listede görünmeyen bir Unity örneği seçme

Listede görünmeyen, bilinen bir Unity oynatıcı varsa, Unity örneği Seç penceresinde **IP giriş** düğmesini kullanabilirsiniz. Hata ayıklayıcıya bağlanmak için çalışan Unity oynatıcının IP adresini ve bağlantı noktasını girin.

Her seferinde IP ve bağlantı noktasını girmeden bu oyuncunun hata ayıklamaya devam etmesini kolaylaştırmak için, **araçlar > seçenekler > Unity > Genel** menüsündeki **hata ayıklama hedeflerini kullan** ayarını etkinleştirin.

![Kaydedilen hata ayıklama hedeflerini kullan ayarının ekran görüntüsü.](../media/vs/visual-studio-tools-unity-use-saved-debug-targets.png)

Visual Studio, kayıtlı hata ayıklama hedeflerini Unity 'ye ekle düğmesine bir seçenek olarak gösterir.

![Kaydedilen hata ayıklama hedefi ayarının ekran görüntüsü.](../media/vs/visual-studio-tools-unity-saved-target.png)

:::zone-end
:::zone pivot="macos"

- Mac için Visual Studio, üstteki menüden, **işlemek için > çalıştır**' ı seçin. 
- **Işleme İliştir** iletişim kutusunda, alt kısımdaki hata ayıklayıcı açılan menüsünde **Unity hata ayıklayıcı** seçeneğini belirleyin.
- Listeden bir Unity örneği seçin ve **Ekle** düğmesine tıklayın.

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizde DLL hatalarını ayıklama

Birçok Unity geliştiricisi, geliştirme işlevlerinin diğer projelerle kolayca paylaşılması için kod bileşenlerini dış dll 'Ler olarak yazıyor. Unity için Visual Studio Araçları, bu dll 'lerdeki kodun, Unity projenizdeki diğer kodla sorunsuz bir şekilde ayıklanabilmesini kolaylaştırır.

> [!NOTE]
> şu anda Unity için Visual Studio Araçları yalnızca yönetilen dll 'leri destekler. C++ dilinde yazılmış olanlar gibi yerel kod dll 'Lerinde hata ayıklamayı desteklemez.

Burada açıklanan senaryo kaynak koda sahip olduğunuzu varsayar. Yani, kendi birinci taraf kodunuzu geliştirdiğinizi veya yeniden kullandığınızı veya bir üçüncü taraf kitaplığına kaynak kodu kullandığınızı ve bunu bir DLL olarak Unity projenizde dağıtmayı planladığınızı unutmayın. Bu senaryo, kaynak kodu olmayan bir DLL 'nin hata ayıklamasını tanımlamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan bir yönetilen DLL projesinde hata ayıklamak için

1. mevcut DLL projenizi Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümüne ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenleri içeren yeni bir yönetilen DLL projesi başlatıyorsunuz olabilirsiniz; bu durumda, bunun yerine Visual Studio çözümüne yeni bir yönetilen DLL projesi ekleyebilirsiniz.

   ![> var olan öğe Ekle menüsünün ekran görüntüsü.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   her iki Unity için Visual Studio Araçları durumda da, proje başvurusunu ve çözüm dosyalarını yeniden oluşturmak zorunda olsa bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity Framework profiline başvurun. Visual Studio ' de, DLL projesinin özelliklerinde, **hedef framework** özelliğini, kullanmakta olduğunuz Unity çerçevesi sürümüne ayarlayın. Bu, projenizin hedeflediği, Unity Full, mikro veya Web temel sınıf kitaplıkları gibi API uyumluluğuyla eşleşen Unity temel sınıf kitaplığıdır. Bu, DLL 'nizin diğer çerçeveler veya uyumluluk düzeylerinde bulunan ancak kullanmakta olduğunuz Unity çerçevesi sürümünde mevcut olmayan çerçeve yöntemlerini aramasını engeller.

> [!NOTE]
> Yalnızca Unity 'nin eski çalışma zamanını kullanıyorsanız, şunlar gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, bu adanmış 3,5 profillerini artık kullanmanız gerekmez. Unity sürümünüz ile uyumlu bir .NET 4. x profili kullanın.

   ![Visual Studio bir proje için seçme hedef çerçevesinin ekran görüntüsü.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. DLL 'yi Unity projenizin varlık klasörüne kopyalayın. Unity 'de varlıklar, çalışma zamanında yüklenebilmeleri için paketlenmiş ve Unity uygulamanız ile birlikte dağıtılan dosyalardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık olarak dağıtılması için Unity Düzenleyicisi, dll 'Lerin Unity projenizdeki varlıklar klasörünün içine yerleştirilmesi gerekir. Bunu iki şekilde yapabilirsiniz:

   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.

   DLL 'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kodu formuyla eşlediklerinden, PDB dosyaları hata ayıklama için gereklidir. eski çalışma zamanını hedefliyorsanız Unity için Visual Studio Araçları, eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi olan dll. MDB dosyasını oluşturmak için dll ve PDB 'den bilgi kullanacaktır. yeni bir çalışma zamanını hedefliyorsanız ve taşınabilir-PDB kullanıyorsanız, yeni Unity çalışma zamanı yerel olarak taşınabilir-pdb 'leri tüketebileceği için Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmayı denemeyecektir.

   PDB oluşturma hakkında daha fazla bilgiyi [burada](/visualstudio/debugger/how-to-set-debug-and-release-configurations)bulabilirsiniz. Yeni çalışma zamanını hedefliyorsanız, taşınabilir-PDB ' yi düzgün bir şekilde oluşturmak için "hata ayıklama bilgileri" ın "taşınabilir" olarak ayarlandığından emin olun. Eski çalışma zamanını hedefliyorsanız, "Full" kullanmanız gerekir.

4. Kodunuzda hata ayıklayın. Artık DLL kaynak kodunuzda, Unity projenizin kaynak kodu ile birlikte hata ayıklama yapabilir ve kesme noktaları ve kod üzerinden atlama gibi tüm hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio işlevselliği için Unity araçlarına, klavye kısayollarını kullanarak hızlı bir şekilde erişebilirsiniz. Mevcut kısayolların özeti aşağıda verilmiştir.

:::zone pivot="windows"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**CTRL** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity Project gezginini açın|**Alt** + **SHIFT** + **E**|**View. Unityprojecbir**|
|Unity belgelerine erişin|**CTRL** + **Alt** + **A, CTRL** + **H**|**Help. UnityAPIReference**|
|Unity hata ayıklayıcıya (oynatıcı veya düzenleyici) iliştirme|**_Varsayılan değer yok_**|**Debug. AttachUnityDebugger**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio klavye kısayollarını belirleme ve özelleştirme](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

:::zone-end
:::zone pivot="macos"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**Cmd** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity belgelerine erişin|**Cmd + '**|**Help. UnityAPIReference**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. IDE 'yi [Özelleştirme](/visualstudio/mac/customizing-the-ide#key-bingings).

:::zone-end

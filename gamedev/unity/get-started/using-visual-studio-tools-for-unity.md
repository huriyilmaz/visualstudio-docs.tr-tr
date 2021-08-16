---
title: Unity için Visual Studio Araçları | Microsoft Docs
description: Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı öğrenin. Unity geliştirmesi için Visual Studio hata ayıklayıcısını da kullanın.
ms.custom: ''
ms.date: 07/03/2018
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
ms.openlocfilehash: 6fa58bb6050c1d2dbd33b429c2cda6597b3e8e22c3f7dc48b1acc39a1746993a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351315"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde, Unity için Visual Studio Araçları'nin tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirmesi için Visual Studio hata ayıklayıcısını kullanmayı öğrenirsiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Unity betiklerini Visual Studio

Bu Visual Studio Unity için dış düzenleyici olarak [ayarlanırsa, Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio)düzenleyicisinden bir betiği çift tıklamak otomatik olarak başlatılır veya Visual Studio ve seçilen betiği açar.

Alternatif olarak, Unity'de Visual Studio **C#** Aç menüsünü seçerek kaynak düzenleyicide açık betik > betik Project açabilirsiniz.

:::zone pivot="windows"
![C# projesini Visual Studio](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![C# projesini Mac için Visual Studio](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Unity belgelerine erişim

Unity betik belgelerine hızlı bir şekilde erişmek için Visual Studio. Api Unity için Visual Studio Araçları yerel olarak bulamazsa, çevrimiçi olarak bulmaya dener.

:::zone pivot="windows"
- Bu Visual Studio, imleci öğrenmek istediğiniz Unity API'sini vurgulayın veya üzerine yerleştirin, **ardından Ctrl** + **Alt** + **M**, **Ctrl** H tuşlarına + **basın**
- Tuş bağlaması yerine **Yardım > Unity API Başvurusu** menüsünü de kullanabilirsiniz.
![Visual Studio'daki Unity API Başvurusu menüsü](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Bu Mac için Visual Studio, imleci öğrenmek istediğiniz Unity API'sini vurgulayın veya üzerine yerleştirerek **Cmd'ye** + **basın**
- Tuş bağlaması yerine **Yardım > Unity API Başvurusu** menüsünü de kullanabilirsiniz.
![Mac için Visual Studio'daki Unity API Başvurusu menüsü](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>Unity API İletileri için IntelliSense

Intellisense kod tamamlama, MonoBehaviour betikleri içinde Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API'sini öğrenme konusunda yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. İmleci, sınıfından türeten bir sınıfın gövdesinin içindeki yeni bir satıra `MonoBehaviour` yerleştirebilirsiniz.

2. Gibi bir Unity iletinin adını yazmaya `OnTriggerEnter` başlayın.

3. **"ontri**" harfleri yazıldıktan sonra IntelliSense önerilerinin listesi görüntülenir.

:::zone pivot="windows"

![IntelliSense'i Visual Studio](../media/vs/intellisense-example.png)  

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

![Visual Studio'a IntelliSense'den Unity iletisi Visual Studio](../media/vs/vstu-intellisense2.png)

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

![Visual Studio'daki monobehavior sihirbazı iletişim kutusu.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![Mac için Visual Studio'daki monobehavior sihirbazı iletişim kutusu.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Unity Project Gezgini
Unity Project Gezgini tüm Unity proje dosyalarınızı ve dizinlerinizi Unity Düzenleyicisi'nde olduğu gibi gösterir. Bu, Unity betiklerinizi projelerde ve Visual Studio Çözüm Gezgini oluşturulan bir çözümde düzenleyen normal komut dosyalarıyla gezinmekten Visual Studio.

:::zone pivot="windows"
- Ana menü Visual Studio Unity > **Gezgini'ni Project seçin.** Klavye kısayolu: **Alt** + **Shift** + **E** 
 ![ Unity Project Gezgini penceresini görüntüleme.](../media/vs/unity-project-explorer.png)
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
![Visual Studio'da Oynat'a tıklayın](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. Bağlan Visual Studio Düğmesine tıklayarak Unity'ye **tıklayın** veya Komut **+ Dönüş veya** **F5 yazın.**
![Mac için Visual Studio'da Oynat'a tıklayın](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Unity'ye geçiş yapmak **ve oynat** düğmesine tıklayarak oyunu düzenleyicide çalıştırın.
:::zone pivot="windows"
![Windows'da Unity'de Oynat'a tıklayın](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![macOS üzerinde Unity'de Oynat'a tıklayın](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Oyun Visual Studio'a bağlıyken Unity düzenleyicisinde çalışırken, karşılaşılan herhangi bir kesme noktası oyunun yürütülmesini duraklatacak ve oyunun kesme noktasıyla karşılaştığı kod hattını Visual Studio.

#### <a name="stop-debugging"></a>Hata ayıklamayı durdurma

:::zone pivot="windows"

Visual Studio'da Durdur düğmesine tıklayın veya Shift + F5 klavye **kısayolunu kullanın.** 
![Dosyada Durdur'a Visual Studio](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Mac için Visual Studio'da Durdur düğmesine tıklayın veya **Shift + Komut + Return tuşlarına basın.** 
![Dosyada Durdur'a Mac için Visual Studio](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Hata ayıklamada hata ayıklama hakkında daha fazla Visual Studio için bkz. Hata [Ayıklayıcısı'Visual Studio bakın.](/debugger/debugger-feature-tour.md)

#### <a name="attach-to-unity-and-play"></a>Unity ve Play'e ekleme

Daha fazla kolaylık sağlamak için Unity'ye **Ekle düğmesini Unity'ye** **Ekle ve Oynat moduna değiştirebilirsiniz.**

:::zone pivot="windows"

1. Unity'ye **Ekle düğmesinin** yanındaki **küçük aşağı oka** tıklayın.
2. Açılan **menüden Unity'ye Ekle** ve Oynat'ı seçin.
   ![Dosya ekleme ve Visual Studio](../media/vs/vstu-attach-and-play.png)

Oynat düğmesi Unity'ye Ekle **ve Oynat olarak etiketlenmiş olur.** Bu düğmeye tıklarsanız veya **F5** klavye kısayolunu kullanarak artık otomatik olarak Unity düzenleyicisine geçiş yapılır ve hata ayıklayıcının ek olarak oyun düzenleyicide Visual Studio çalışır.

:::zone-end
:::zone pivot="macos"
Hata ayıklamayı başlatma ve Unity düzenleyicisini oynatma, Unity'ye Ekle ve Oynat Mac için Visual Studio doğrudan tek bir adımda **tamamlanır.**

![Unity'ye Ekle'yi seçin ve Mac için Visual Studio](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> Unity'ye Ekle ve Oynat **yapılandırmasını kullanarak** hata ayıklamaya başladıysanız, Durdur **düğmesi** Unity Düzenleyicisi'ni de durdurur.

### <a name="debug-unity-player-builds&quot;></a>Unity oynatıcı derlemeleri için hata ayıklama

Unity oyuncularının geliştirme derlemelerinin hata ayıklaması için Visual Studio.

#### <a name=&quot;enable-script-debugging-in-a-unity-player&quot;></a>Unity oynatıcıda betik hata ayıklamayı etkinleştirme

1. Unity'de Dosya ve Derleme Ayarlar'ı **seçerek Derleme >'Ayarlar.**
2. Derleme derlemesi Ayarlar Geliştirme **Derlemesi ve Betik Hata** **Ayıklama onay** kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırma.](../media/vs/vstu-debugging-build-settings.png &quot;vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı eklemek için bir Unity örneği seçin

:::zone pivot="windows"

- Bu Visual Studio ana menüden Unity Hata Ayıklayıcısını **Ekle'> Ayıkla'ya tıklayın.**

   ![Unity'nin hata ayıklayıcısını ekleme.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity Örneği Seç iletişim** kutusunda bağlanabilirsiniz her Unity örneği hakkında bazı bilgiler görüntülenir.

   ![Bağlanmak için bir Unity örneği seçin.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Unity'nin bu örneğinde çalışan Unity projesinin adı.

   **Makine** Unity'nin bu örneğinin üzerinde çalıştır olduğu bilgisayarın veya cihazın adı.

   **Unity'nin**  bu örneği Unity Düzenleyicisi'nin bir parçası olarak çalışıyorsa Düzenleyiciyazın; **Unity'nin** bu örneği tek başına bir oyuncu ise oynatıcı.

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Unity için Visual Studio Araçları ve Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınız buna izin vermek için kural gerekebilir. Gerekirse, bir istem görebilirsiniz, bu durumda, VSTU ve Unity 'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.

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

   ![Varolan DLL projenizi çözüme ekleyin.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   her iki Unity için Visual Studio Araçları durumda da, proje başvurusunu ve çözüm dosyalarını yeniden oluşturmak zorunda olsa bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity Framework profiline başvurun. Visual Studio ' de, DLL projesinin özelliklerinde, **hedef framework** özelliğini, kullanmakta olduğunuz Unity çerçevesi sürümüne ayarlayın. Bu, projenizin hedeflediği, Unity Full, mikro veya Web temel sınıf kitaplıkları gibi API uyumluluğuyla eşleşen Unity temel sınıf kitaplığıdır. Bu, DLL 'nizin diğer çerçeveler veya uyumluluk düzeylerinde bulunan ancak kullanmakta olduğunuz Unity çerçevesi sürümünde mevcut olmayan çerçeve yöntemlerini aramasını engeller.

> [!NOTE]
> Yalnızca Unity 'nin eski çalışma zamanını kullanıyorsanız, şunlar gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, bu adanmış 3,5 profillerini artık kullanmanız gerekmez. Unity sürümünüz ile uyumlu bir .NET 4. x profili kullanın.

   ![DLL 'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. DLL 'yi Unity projenizin varlık klasörüne kopyalayın. Unity 'de varlıklar, çalışma zamanında yüklenebilmeleri için paketlenmiş ve Unity uygulamanız ile birlikte dağıtılan dosyalardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık olarak dağıtılması için Unity Düzenleyicisi, dll 'Lerin Unity projenizdeki varlıklar klasörünün içine yerleştirilmesi gerekir. Bunu iki şekilde yapabilirsiniz:

   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.

   DLL 'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kodu formuyla eşlediklerinden, PDB dosyaları hata ayıklama için gereklidir. eski çalışma zamanını hedefliyorsanız Unity için Visual Studio Araçları, eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi olan dll. MDB dosyasını oluşturmak için dll ve PDB 'den bilgi kullanacaktır. yeni bir çalışma zamanını hedefliyorsanız ve taşınabilir-PDB kullanıyorsanız, yeni Unity çalışma zamanı yerel olarak taşınabilir-pdb 'leri tüketebileceği için Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmayı denemeyecektir.

   PDB oluşturma hakkında daha fazla bilgiyi [burada](/debugger/how-to-set-debug-and-release-configurations.md)bulabilirsiniz. Yeni çalışma zamanını hedefliyorsanız, taşınabilir-PDB ' yi düzgün bir şekilde oluşturmak için "hata ayıklama bilgileri" ın "taşınabilir" olarak ayarlandığından emin olun. Eski çalışma zamanını hedefliyorsanız, "Full" kullanmanız gerekir.

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

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio klavye kısayollarını belirleme ve özelleştirme](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

:::zone-end
:::zone pivot="macos"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**Cmd** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity belgelerine erişin|**Cmd + '**|**Help. UnityAPIReference**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. IDE 'yi [Özelleştirme](/mac/customizing-the-ide#key-bingings).

:::zone-end

---
title: Unity için Visual Studio Araçları kullanma | Microsoft Docs
description: Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı öğrenin. Ayrıca, Unity geliştirmesi için Visual Studio hata ayıklayıcısını kullanın.
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
ms.openlocfilehash: 9a89f83ecaa4545eb6151c7a92e76a08708c3855
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341785"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio 'da Unity betikleri açın

[Unity için dış düzenleyici olarak](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio)Visual Studio ayarlandığında, Unity düzenleyicisinden bir betiğe çift tıklamak otomatik olarak başlatılır veya Visual Studio 'ya geçer ve seçilen betiği açar.

Alternatif olarak, Unity 'de **C# proje menüsünü aç > varlıklar** ' ı seçerek Visual Studio 'yu kaynak düzenleyicide açık betik olmadan açabilirsiniz.

:::zone pivot="windows"
![Visual Studio 'da C# projesi aç](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![Mac için Visual Studio C# projesi açın](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Unity belge erişimi

Unity betik belgelerine Visual Studio 'dan hızlıca erişebilirsiniz. API belgelerini yerel olarak bulamazsa Unity için Visual Studio Araçları çevrimiçi bulmaya çalışır.

:::zone pivot="windows"
- Visual Studio 'da imleci, hakkında bilgi edinmek istediğiniz Unity API 'sinin üzerine getirin veya yerleştirin, sonra **CTRL** + **alt** + **M** , **CTRL** + **H** tuşlarına basın
- KeyBinding yerine, **yardım > UNITY API başvurusu** menüsünü de kullanabilirsiniz.
![Visual Studio 'da Unity API başvuru menüsü](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Mac için Visual Studio, imleci, hakkında bilgi edinmek istediğiniz Unity API 'sinin üzerine getirin veya yerleştirin, sonra **cmd** + **'** tuşuna basın
- KeyBinding yerine, **yardım > UNITY API başvurusu** menüsünü de kullanabilirsiniz.
![Mac için Visual Studio 'da Unity API başvuru menüsü](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>Unity API Iletileri için IntelliSense

IntelliSense kod tamamlama, tek davranış betiklerine Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API 'sini öğrenmeye yardımcı olur. Unity iletileri için IntelliSense 'i kullanmak için:

1. İmleci, ' den türetilen bir sınıfın gövdesinin içine yeni bir satıra yerleştirin `MonoBehaviour` .

2. Bir Unity iletisinin adını yazmaya başlayın, örneğin `OnTriggerEnter` .

3. " **Ontri** " harfleri yazıldıktan sonra, bir IntelliSense önerisi listesi görüntülenir.

:::zone pivot="windows"

![Visual Studio 'da IntelliSense kullanma](../media/vs/intellisense-example.png)  

:::zone-end

4. Listedeki seçim üç şekilde değiştirilebilir:

    - **Yukarı** ve **aşağı** ok tuşlarıyla.

    - İstenen öğenin üzerine fareyle tıklanarak.

    - İstenen öğenin adını yazmaya devam edin.

5. IntelliSense, gerekli parametreler dahil olmak üzere seçili Unity iletisini ekleyebilir:

    - **Sekmesine** basarak.

    - **ENTER** tuşuna basarak.

    - Seçili öğeye çift tıklayarak.

:::zone pivot="windows"

![Visual Studio 'da IntelliSense 'den Unity iletisi ekleme](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior betik Sihirbazı

Tek davranış Sihirbazı ' nı kullanarak tüm Unity API yöntemlerinin bir listesini görüntüleyebilir ve boş bir tanımı hızlıca uygulayabilirsiniz. Bu özellik özellikle, **Yöntem açıklamalarını oluştur** seçeneği etkinken, Unity API 'sinde nelerin kullanılabildiğini öğrenseniz yararlı olur.

MonoBehavior sihirbazıyla boş MonoBehavior yöntemi tanımları oluşturmak için:

1. Visual Studio 'da yöntemlerin eklenmesini istediğiniz yere konumlandırın, sonra **Ctrl** + **Shift** + MonoBehavior sihirbazını başlatmak için CTRL SHIFT **e** tuşlarına basın. Mac için Visual Studio ' de **cmd** + **Shift** + **e** tuşlarına basın.

2. **Betik yöntemleri oluştur** penceresinde, eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü seçmek için **Framework sürümü** açılan listesini kullanın.

4. Varsayılan olarak, Yöntemler İmlecin konumuna eklenir. Alternatif olarak, **ekleme noktası** açılır listesinin değerini istediğiniz konuma değiştirerek, sınıfınıza zaten uygulanmış herhangi bir yöntemden sonra bunları eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemlere yorum oluşturmasını istiyorsanız, **Yöntem açıklamaları oluştur** onay kutusunu işaretleyin. Bu yorumlar, yöntemin ne zaman çağrıldığını ve genel sorumlulukların ne zaman olduğunu anlamanıza yardımcı olmak için tasarlanmıştır.

6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.

:::zone pivot="windows"

![Visual Studio 'daki MonoBehavior Sihirbazı iletişim kutusu.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![Mac için Visual Studio içindeki MonoBehavior Sihirbazı iletişim kutusu.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Unity Proje Gezgini
Unity Proje Gezgini tüm Unity proje dosyalarınızı ve dizinlerinizi Unity düzenleyiciyle aynı şekilde gösterir. Bu, Unity betiklerinizde, bunları projeler ve Visual Studio tarafından oluşturulan bir çözüme düzenleyen normal Visual Studio Çözüm Gezgini ile gezinmeden farklıdır.

:::zone pivot="windows"
- Ana Visual Studio menüsünde **görünüm > Unity Proje Gezgini** ' ni seçin. Klavye kısayolu: **alt** + **Shift** + **E** 
 ![ , Unity Proje Gezgini penceresini görüntüleyin.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- Mac için Visual Studio, bir Unity projesi açıldığında Çözüm Bölmesi otomatik olarak bu şekilde davranır.
:::zone-end
## <a name="unity-debugging"></a>Unity hata ayıklaması

Unity için Visual Studio Araçları, Visual Studio 'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için hem Düzenleyici hem de oyun betiklerinin hatalarını ayıklamanızı sağlar.

### <a name="debug-in-the-unity-editor"></a>Unity düzenleyicisinde hata ayıklama

#### <a name="start-debugging"></a>Hata ayıklamayı Başlat
:::zone pivot="windows"

1. **Unity 'ye Ekle** etiketli **oynat** düğmesine tıklayarak ve **F5** klavye kısayolunu kullanarak Visual Studio 'yu Unity 'ye bağlayın.
![Visual Studio 'da Yürüt ' e tıklayın](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. **Oynat** düğmesine tıklayarak Visual Studio 'yu Unity 'ye bağlayın veya **Command + Return** ya da **F5** yazın.
![Mac için Visual Studio içinde oynat ' ı tıklatın](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.
:::zone pivot="windows"
![Windows 'da Unity 'de oynat ' a tıklayın](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![MacOS 'ta Unity 'de Yürüt ' e tıklayın](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. Oyun, Visual Studio 'ya bağlıyken Unity Düzenleyicisi 'nde çalışırken, karşılaştığı herhangi bir kesme noktası oyunun yürütülmesini duraklatır ve oyunun Visual Studio 'daki kesme noktasına isabet ettiği kod satırını getirir.

#### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

:::zone pivot="windows"

Visual Studio 'da **Durdur** düğmesine tıklayın veya klavye kısayolunun **SHIFT + F5** tuşlarını kullanın.
![Visual Studio 'da Durdur ' a tıklayın](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Mac için Visual Studio **Durdur** düğmesine tıklayın veya **SHIFT + Command + Return** tuşlarına basın.
![Mac için Visual Studio Durdur ' a tıklayın](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcıya ilk bakış](/debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Unity 'ye Ekle ve Yürüt

Ek kolaylık sağlamak için Unity 'ye **Ekle** düğmesini, **Unity ve Play moduna eklemek** için değiştirebilirsiniz.

:::zone pivot="windows"

1. **Unity 'ye Ekle** düğmesinin yanındaki küçük **aşağı oka** tıklayın.
2. **Unity 'ye Ekle ve açılır menüden Oynat ' ı** seçin.
   ![Visual Studio 'da iliştirme ve yürütme](../media/vs/vstu-attach-and-play.png)

Oynat düğmesi, **Unity 'ye Ekle ve Yürüt** şeklinde etiketlenmiş hale gelir. Bu düğmeye tıkladığınızda veya klavye kısayolunun **F5** 'i kullanmak artık Unity düzenleyicisine otomatik olarak geçer ve Visual Studio hata ayıklayıcıyı eklemenin yanı sıra oyunu düzenleyicide çalıştırır.

:::zone-end
:::zone pivot="macos"
Unity 'nin hata ayıklamasının başlaması ve Unity Düzenleyicisi 'nin yürütülmesi, **Unity 'ye Ekle ve Çalıştır** yapılandırması seçilerek Mac için Visual Studio doğrudan tek bir adımda tamamlanabilir.

![Unity 'ye Ekle ve Mac için Visual Studio oynat ' ı seçin](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> **Unity 'ye Ekle ve Çalıştır** yapılandırmasını kullanarak hata ayıklamaya başladıysanız, **Durdur** düğmesi de Unity düzenleyicisini durdurur.

### <a name="debug-unity-player-builds"></a>Unity oynatıcı Derlemeleriyle hata ayıkla

Visual Studio ile Unity oynatıcıların geliştirme Derlemeleriyle ilgili hata ayıklaması yapabilirsiniz.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity Player 'da betik hata ayıklamasını etkinleştirme

1. Unity 'de **dosya > yapı ayarları** ' nı seçerek yapı ayarlarını açın.
2. Derleme ayarları penceresinde, **geliştirme derlemesi** ve **betik hata ayıklama** onay kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../media/vs/vstu-debugging-build-settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı iliştirmek için bir Unity örneği seçin

:::zone pivot="windows"

- Visual Studio 'da, ana menüdeki **hata ayıkla > Unity hata ayıklayıcı Ekle** ' yi seçin.

   ![Unity hata ayıklayıcısını iliştirin.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity örneği Seç** iletişim kutusu, bağlandığınız her Unity örneğiyle ilgili bazı bilgileri görüntüler.

   ![Bağlanılacak Unity örneğini seçin.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Unity 'nin bu örneğinde çalışan Unity projesinin adı.

   **Makine** Bu Unity örneğinin üzerinde çalıştığı bilgisayarın veya cihazın adı.

   Unity 'in bu örneği Unity Düzenleyicisi 'nin bir parçası olarak çalışıyorsa, **tür** **Düzenleyici** ; Bu Unity örneği tek başına bir oynatıcı ise **oynatıcı** .

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Unity için Visual Studio Araçları ve Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınız buna izin vermek için kural gerekebilir. Gerekirse, bir istem görebilirsiniz, bu durumda, VSTU ve Unity 'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.

:::zone-end
:::zone pivot="macos"

- Mac için Visual Studio, üstteki menüden, **işlemek için > Çalıştır** ' ı seçin. 
- **Işleme İliştir** iletişim kutusunda, alt kısımdaki hata ayıklayıcı açılan menüsünde **Unity hata ayıklayıcı** seçeneğini belirleyin.
- Listeden bir Unity örneği seçin ve **Ekle** düğmesine tıklayın.

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizde DLL hatalarını ayıklama

Birçok Unity geliştiricisi, geliştirme işlevlerinin diğer projelerle kolayca paylaşılması için kod bileşenlerini dış dll 'Ler olarak yazıyor. Unity için Visual Studio Araçları, bu DLL 'Lerdeki kodun, Unity projenizdeki diğer kodla sorunsuz bir şekilde ayıklanabilmesini kolaylaştırır.

> [!NOTE]
> Şu anda Unity için Visual Studio Araçları yalnızca yönetilen DLL 'Leri destekler. C++ dilinde yazılmış olanlar gibi yerel kod dll 'Lerinde hata ayıklamayı desteklemez.

Burada açıklanan senaryo kaynak koda sahip olduğunuzu varsayar. Yani, kendi birinci taraf kodunuzu geliştirdiğinizi veya yeniden kullandığınızı veya bir üçüncü taraf kitaplığına kaynak kodu kullandığınızı ve bunu bir DLL olarak Unity projenizde dağıtmayı planladığınızı unutmayın. Bu senaryo, kaynak kodu olmayan bir DLL 'nin hata ayıklamasını tanımlamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan bir yönetilen DLL projesinde hata ayıklamak için

1. Mevcut DLL projenizi Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümüne ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenleri içeren yeni bir yönetilen DLL projesi başlatıyorsunuz olabilirsiniz; Bu durumda, bunun yerine Visual Studio çözümüne yeni bir yönetilen DLL projesi ekleyebilirsiniz.

   ![Varolan DLL projenizi çözüme ekleyin.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   Her iki Unity için Visual Studio Araçları durumda da, proje başvurusunu ve çözüm dosyalarını yeniden oluşturmak zorunda olsa bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity Framework profiline başvurun. Visual Studio 'da, DLL projesinin özelliklerinde, **hedef Framework** özelliğini kullandığınız Unity çerçevesi sürümü olarak ayarlayın. Bu, projenizin hedeflediği, Unity Full, mikro veya Web temel sınıf kitaplıkları gibi API uyumluluğuyla eşleşen Unity temel sınıf kitaplığıdır. Bu, DLL 'nizin diğer çerçeveler veya uyumluluk düzeylerinde bulunan ancak kullanmakta olduğunuz Unity çerçevesi sürümünde mevcut olmayan çerçeve yöntemlerini aramasını engeller.

> [!NOTE]
> Yalnızca Unity 'nin eski çalışma zamanını kullanıyorsanız, şunlar gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, bu adanmış 3,5 profillerini artık kullanmanız gerekmez. Unity sürümünüz ile uyumlu bir .NET 4. x profili kullanın.

   ![DLL 'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. DLL 'yi Unity projenizin varlık klasörüne kopyalayın. Unity 'de varlıklar, çalışma zamanında yüklenebilmeleri için paketlenmiş ve Unity uygulamanız ile birlikte dağıtılan dosyalardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık olarak dağıtılması için Unity Düzenleyicisi, dll 'Lerin Unity projenizdeki varlıklar klasörünün içine yerleştirilmesi gerekir. Bunu iki şekilde yapabilirsiniz:

   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.

   DLL 'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kodu formuyla eşlediklerinden, PDB dosyaları hata ayıklama için gereklidir. Eski çalışma zamanını hedefliyorsanız, Unity için Visual Studio Araçları dll ve PDB 'den DLL oluşturmak için bu bilgileri kullanır. MDB dosyası, eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembolü biçimidir. Yeni bir çalışma zamanını hedefliyorsanız ve taşınabilir-PDB kullanıyorsanız, yeni Unity çalışma zamanı yerel olarak taşınabilir-pdb 'leri tüketebileceği için Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmayı denemeyecektir.

   PDB oluşturma hakkında daha fazla bilgiyi [burada](/debugger/how-to-set-debug-and-release-configurations.md)bulabilirsiniz. Yeni çalışma zamanını hedefliyorsanız, taşınabilir-PDB ' yi düzgün bir şekilde oluşturmak için "hata ayıklama bilgileri" ın "taşınabilir" olarak ayarlandığından emin olun. Eski çalışma zamanını hedefliyorsanız, "Full" kullanmanız gerekir.

4. Kodunuzda hata ayıklayın. Artık DLL kaynak kodunuzda, Unity projenizin kaynak kodu ile birlikte hata ayıklama yapabilir ve kesme noktaları ve kod üzerinden atlama gibi tüm hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio işlevselliği için Unity araçlarına, klavye kısayollarını kullanarak hızlıca erişebilirsiniz. Mevcut kısayolların özeti aşağıda verilmiştir.

:::zone pivot="windows"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**CTRL** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity proje Gezginini açın|**Alt** + **SHIFT** + **E**|**View. Unityprojecbir**|
|Unity belgelerine erişin|**CTRL** + **Alt** + **A, CTRL** + **H**|**Help. UnityAPIReference**|
|Unity hata ayıklayıcıya (oynatıcı veya düzenleyici) iliştirme|**_Varsayılan değer yok_**|**Debug. AttachUnityDebugger**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio 'da klavye kısayollarını belirleme ve özelleştirme](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

:::zone-end
:::zone pivot="macos"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**Cmd** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity belgelerine erişin|**Cmd + '**|**Help. UnityAPIReference**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. IDE 'yi [Özelleştirme](/mac/customizing-the-ide#key-bingings).

:::zone-end

---
title: Unity için Visual Studio Araçları kullanma | Microsoft Docs
description: Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı öğrenin. ayrıca, Unity geliştirmesi için Visual Studio hata ayıklayıcıyı kullanın.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725504"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

bu bölümde Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirme için Visual Studio hata ayıklayıcıyı kullanmayı öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Unity betiklerini Visual Studio açın

Visual Studio [unity için dış düzenleyici olarak](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-to-use-visual-studio)ayarlandıktan sonra, unity düzenleyiciden bir betiğe çift tıklanması otomatik olarak başlatılır veya Visual Studio ve seçilen betiği açar.

alternatif olarak, Unity 'de **C# Project menüsünü aç > varlıkları** seçerek kaynak düzenleyicide açık betik olmadan Visual Studio açabilirsiniz.

:::zone pivot="windows"
![Visual Studio C# projesi açın](../media/vs/vstu-open-csharp-project.png)
:::zone-end
:::zone pivot="macos"
![Mac için Visual Studio C# projesi açın](../media/vsm/vstu-open-csharp-project.png)
:::zone-end

## <a name="unity-documentation-access"></a>Unity belge erişimi

Unity betik belgelerine hızla Visual Studio erişebilirsiniz. apı belgelerini yerel olarak bulamazsa Unity için Visual Studio Araçları çevrimiçi bulmaya çalışır.

:::zone pivot="windows"
- Visual Studio, imleci, hakkında bilgi edinmek istediğiniz Unity apı 'sinin üzerine getirin veya yerleştirin, sonra **ctrl** + **Alt** + **M**, **ctrl** + **H** tuşlarına basın
- KeyBinding yerine, **yardım > UNITY API başvurusu** menüsünü de kullanabilirsiniz.
![Visual Studio 'da Unity API başvuru menüsü](../media/vs/help-unity-documentation.png)
:::zone-end
:::zone pivot="macos"
- Mac için Visual Studio, imleci, hakkında bilgi edinmek istediğiniz Unity apı 'sinin üzerine getirin veya yerleştirin, sonra **Cmd** + **'** tuşuna basın
- KeyBinding yerine, **yardım > UNITY API başvurusu** menüsünü de kullanabilirsiniz.
![Mac için Visual Studio 'da Unity apı başvuru menüsü](../media/vsm/help-unity-documentation.png)
:::zone-end

## <a name="intellisense-for-unity-api-messages"></a>Unity API Iletileri için IntelliSense

IntelliSense kod tamamlama, tek davranış betiklerine Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API 'sini öğrenmeye yardımcı olur. Unity iletileri için IntelliSense 'i kullanmak için:

1. İmleci, ' den türetilen bir sınıfın gövdesinin içine yeni bir satıra yerleştirin `MonoBehaviour` .

2. Bir Unity iletisinin adını yazmaya başlayın, örneğin `OnTriggerEnter` .

3. "**Ontri**" harfleri yazıldıktan sonra, bir IntelliSense önerisi listesi görüntülenir.

:::zone pivot="windows"

![Visual Studio içinde IntelliSense kullanma](../media/vs/intellisense-example.png)  

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

![Visual Studio içinde IntelliSense 'ten Unity iletisi ekleme](../media/vs/vstu-intellisense2.png)

:::zone-end

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior betik Sihirbazı

Tek davranış Sihirbazı ' nı kullanarak tüm Unity API yöntemlerinin bir listesini görüntüleyebilir ve boş bir tanımı hızlıca uygulayabilirsiniz. Bu özellik özellikle, **Yöntem açıklamalarını oluştur** seçeneği etkinken, Unity API 'sinde nelerin kullanılabildiğini öğrenseniz yararlı olur.

MonoBehavior sihirbazıyla boş MonoBehavior yöntemi tanımları oluşturmak için:

1. Visual Studio, imleci, yöntemlerin eklenmesini istediğiniz yere konumlandırın, sonra  +  + monobehavior sihirbazını başlatmak için Ctrl shıft **e** tuşlarına basın. Mac için Visual Studio ' de **Cmd** + **Shift** + **e** tuşlarına basın.

2. **Betik yöntemleri oluştur** penceresinde, eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü seçmek için **Framework sürümü** açılan listesini kullanın.

4. Varsayılan olarak, Yöntemler İmlecin konumuna eklenir. Alternatif olarak, **ekleme noktası** açılır listesinin değerini istediğiniz konuma değiştirerek, sınıfınıza zaten uygulanmış herhangi bir yöntemden sonra bunları eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemlere yorum oluşturmasını istiyorsanız, **Yöntem açıklamaları oluştur** onay kutusunu işaretleyin. Bu yorumlar, yöntemin ne zaman çağrıldığını ve genel sorumlulukların ne zaman olduğunu anlamanıza yardımcı olmak için tasarlanmıştır.

6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.

:::zone pivot="windows"

![Visual Studio içindeki MonoBehavior Sihirbazı iletişim kutusu.](../media/vs/vstu-monobehavior-wizard.png)
:::zone-end
:::zone pivot="macos"

![Mac için Visual Studio içindeki monobehavior sihirbazı iletişim kutusu.](../media/vsm/vstu-monobehavior-wizard.png)
:::zone-end   

## <a name="unity-project-explorer"></a>Unity Project gezgini
unity Project gezgini, unity düzenleyiciyle aynı şekilde tüm unity proje dosyalarınızı ve dizinlerinizi gösterir. bu, Unity betiklerinizde, bunları projeler ve Visual Studio tarafından oluşturulan bir çözüm olarak düzenleyen normal Visual Studio Çözüm Gezgini ile gezinmeden farklıdır.

:::zone pivot="windows"
- ana Visual Studio menüsünde **görünüm > Unity Project gezgini**' ni seçin. klavye kısayolu: **Alt** + **Shift** + **E** 
 ![ , Unity Project gezgin penceresini görüntüleyin.](../media/vs/unity-project-explorer.png)
:::zone-end
:::zone pivot="macos"
- Mac için Visual Studio, bir Unity projesi açıldığında Çözüm Bölmesi otomatik olarak bu şekilde davranır.
:::zone-end
## <a name="unity-debugging"></a>Unity hata ayıklaması

Unity için Visual Studio Araçları, Visual Studio güçlü hata ayıklayıcısını kullanarak Unity projeniz için hem düzenleyici hem de oyun betiklerinin hatalarını ayıklamanıza olanak tanır.

### <a name="debug-in-the-unity-editor"></a>Unity düzenleyicisinde hata ayıklama

#### <a name="start-debugging"></a>Hata ayıklamayı Başlat
:::zone pivot="windows"

1. unity **'ye ekle** etiketli **oynat** düğmesine tıklayarak unity 'ye Visual Studio Bağlan veya **F5** klavye kısayolunu kullanın.
![Visual Studio içinde oynat ' ı tıklatın](../media/vs/vstu-play-button.png)

:::zone-end
:::zone pivot="macos"

1. **oynat** düğmesine tıklayarak Unity 'ye Visual Studio Bağlan veya **Command + Return** ya da **F5** yazın.
![Mac için Visual Studio içinde oynat ' ı tıklatın](../media/vsm/using-vsmac-tools-unity-image5.png)

:::zone-end

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.
:::zone pivot="windows"
![Windows için Unity 'de oynat ' a tıklayın](../media/vs/vstu-unity-play-button.png)
:::zone-end
:::zone pivot="macos"
![MacOS 'ta Unity 'de Yürüt ' e tıklayın](../media/vsm/using-vsmac-tools-unity-image6.png)
:::zone-end

3. oyun, Visual Studio bağlı durumdayken Unity düzenleyicisinde çalışırken, karşılaştığı herhangi bir kesme noktası oyunun yürütülmesini duraklatır ve oyunun Visual Studio kesme noktasına isabet ettiği kod satırını getirir.

#### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

:::zone pivot="windows"

Visual Studio **durdur** düğmesine tıklayın veya klavye kısayolunun **shıft + F5** tuşlarını kullanın.
![Visual Studio Durdur ' a tıklayın](../media/vs/vstu-stop-debugger.png)

:::zone-end
:::zone pivot="macos"

Mac için Visual Studio **durdur** düğmesine tıklayın veya **shıft + Command + Return** tuşlarına basın.
![Mac için Visual Studio durdur ' a tıklayın](../media/vsm/using-vsmac-tools-unity-image7.png)

:::zone-end

Visual Studio 'de hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcısına](/debugger/debugger-feature-tour.md)bakın.

#### <a name="attach-to-unity-and-play"></a>Unity 'ye Ekle ve Yürüt

Ek kolaylık sağlamak için Unity 'ye **Ekle** düğmesini, **Unity ve Play moduna eklemek** için değiştirebilirsiniz.

:::zone pivot="windows"

1. **Unity 'ye Ekle** düğmesinin yanındaki küçük **aşağı oka** tıklayın.
2. **Unity 'ye Ekle ve açılır menüden Oynat ' ı** seçin.
   ![Visual Studio iliştirme ve yürütme](../media/vs/vstu-attach-and-play.png)

Oynat düğmesi, **Unity 'ye Ekle ve Yürüt** şeklinde etiketlenmiş hale gelir. bu düğmeye tıkladığınızda veya klavye kısayolunun **F5** 'i kullanmak artık Unity düzenleyicisine otomatik olarak geçer ve Visual Studio hata ayıklayıcıyı eklemenin yanı sıra oyunu düzenleyicide çalıştırır.

:::zone-end
:::zone pivot="macos"
unity 'nin hata ayıklamasının başlaması ve unity düzenleyicisi 'nin yürütülmesi, **unity 'ye ekle ve çalıştır** yapılandırması seçilerek Mac için Visual Studio doğrudan tek bir adımda tamamlanabilir.

![Unity 'ye ekle ve Mac için Visual Studio oynat ' ı seçin](../media/vsm/using-vsmac-tools-unity-image8.png)
:::zone-end

> [!NOTE]
> **Unity 'ye Ekle ve Çalıştır** yapılandırmasını kullanarak hata ayıklamaya başladıysanız, **Durdur** düğmesi de Unity düzenleyicisini durdurur.

### <a name="debug-unity-player-builds&quot;></a>Unity oynatıcı Derlemeleriyle hata ayıkla

Visual Studio Unity oynatıcıların geliştirme Derlemeleriyle ilgili hata ayıklaması yapabilirsiniz.

#### <a name=&quot;enable-script-debugging-in-a-unity-player&quot;></a>Unity Player 'da betik hata ayıklamasını etkinleştirme

1. Unity 'de, derleme Ayarlar **dosya > build Ayarlar**' i seçerek açın.
2. derleme Ayarlar penceresinde, **geliştirme derlemesi** ve **betik hata ayıklama** onay kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../media/vs/vstu-debugging-build-settings.png &quot;vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı iliştirmek için bir Unity örneği seçin

:::zone pivot="windows"

- Visual Studio, ana menüdeki **hata ayıkla > Unity hata ayıklayıcı ekle**' yi seçin.

   ![Unity hata ayıklayıcısını iliştirin.](../media/vs/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity örneği Seç** iletişim kutusu, bağlandığınız her Unity örneğiyle ilgili bazı bilgileri görüntüler.

   ![Bağlanılacak Unity örneğini seçin.](../media/vs/vstu-attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Unity 'nin bu örneğinde çalışan Unity projesinin adı.

   **Makine** Bu Unity örneğinin üzerinde çalıştığı bilgisayarın veya cihazın adı.

   Unity 'in bu örneği Unity Düzenleyicisi 'nin bir parçası olarak çalışıyorsa, **tür** **Düzenleyici** ; Bu Unity örneği tek başına bir oynatıcı ise **oynatıcı** .

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Ağ Unity için Visual Studio Araçları Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınıza izin vermek için kural gerekebilir. Gerekirse, VSTU ve Unity'nin iletişim kura çalışması için bağlantıyı yetkilendirmek için bir istemle karşılaşmanız gerekir.

:::zone-end
:::zone pivot="macos"

- Bu Mac için Visual Studio üst menüde Çalıştır'ı seçin **ve > Ekle'yi seçin.** 
- İşleme **Ekle iletişim kutusunda,** alttaki **Hata Ayıklayıcı** açılan menüsünde Unity Hata Ayıklayıcısı seçeneğini belirleyin.
- Listeden bir Unity örneği seçin ve Ekle **düğmesine** tıklayın.

:::zone-end

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizin DLL'sinde hata ayıklama

Birçok Unity geliştiricisi, geliştirecekleri işlevselliğin diğer projelerle kolayca paylaşılamalarını sağlamak için kod bileşenlerini dış URL'ler olarak yazıyor. Unity için Visual Studio Araçları, Unity projenizin diğer kodlarla bu URL'lerde hata ayıklamayı kolaylaştırır.

> [!NOTE]
> Şu anda, Unity için Visual Studio Araçları yönetilen URL'leri destekler. C++ ile yazılanlar gibi yerel kod URL'lerinde hata ayıklamayı desteklemez.

Burada açıklanan senaryoda kaynak kodunuz olduğu varsayılır; yani kendi birinci taraf kodunuzu geliştiriyor veya yeniden kullanıyorsanız ya da kaynak kodunuz üçüncü taraf bir kitapliğe sahipse ve bunu Unity projenize DLL olarak dağıtmayı planlasanız. Bu senaryo, kaynak koduna sahip olmadığınız bir DLL'de hata ayıklamayı açıklamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projesinde kullanılan yönetilen DLL projesinde hata ayıklamak için

1. Mevcut DLL projenizi, Visual Studio tarafından oluşturulan çözüme Unity için Visual Studio Araçları. Daha az yaygın olarak, Unity projenize kod bileşenlerini içeren yeni bir yönetilen DLL projesi başlatıyor olabilir; Bu durumda, bunun yerine yeni bir yönetilen DLL projesini Visual Studio eklersiniz.

   ![Mevcut DLL projenizi çözüme ekleyin.](../media/vs/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")

   Her iki Unity için Visual Studio Araçları proje ve çözüm dosyalarını yeniden oluşturması gerekse bile proje başvurularını korumanız gerekir, bu nedenle bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity framework profiline bakın. Bu Visual Studio DLL projesinin özelliklerinde **Target framework** özelliğini kullanmakta olan Unity framework sürümüne ayarlayın. Bu, Unity tam, mikro veya web temel sınıf kitaplıkları gibi projenizin hedefle olduğu API uyumluluğuyla eşleşen Unity Temel Sınıf Kitaplığı'dır. Bu, DLL'nizin diğer çerçevelerde veya uyumluluk düzeylerinde mevcut olan ancak kullanmakta olan Unity framework sürümünde mevcut olmayan çerçeve yöntemlerini çağırmasına engel olur.

> [!NOTE]
> Aşağıdakiler yalnızca Unity'nin eski çalışma zamanı kullanıyorsanız gereklidir. Yeni Unity çalışma zamanı kullanıyorsanız, artık bu ayrılmış 3.5 profillerini kullanmana gerek yoktur. Unity sürümünüzle uyumlu bir .NET 4.x profili kullanın.

   ![DLL'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../media/vs/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")

3. DLL'i Unity projenizin Varlık klasörüne kopyalayın. Unity'de varlıklar, çalışma zamanında yüklensin diye Unity uygulamanız ile birlikte paketlenmiş ve dağıtılan dosyalardır. URL'ler çalışma zamanında bağlı olduğu için, URL'lerin varlıklar olarak dağıtılması gerekir. Unity Düzenleyicisi' nin varlık olarak dağıtılması için, UNITY'lerin Unity projenizin Assets klasörüne konmalarını gerektirir. Bunu iki şekilde yapabilirsiniz:

   - DLL projenizin derleme ayarlarını, çıkış klasöründeki çıkış DLL'sini ve PDB dosyalarını Unity projenizin **Assets** klasörüne kopyalanan bir post-built görevi içerecek şekilde değiştirin.

   - DLL projenizin derleme ayarlarını değiştirerek çıkış klasörünü Unity projenizin **Assets** klasörü olarak ayarlayın. Hem DLL hem de PDB dosyaları **Varlıklar klasörüne yerleştirilir.**

   DLL'nin hata ayıklama sembollerini içerdiği ve DLL kodunu kaynak kod formuyla eşleyebilecekleri için PDB dosyaları hata ayıklama için gereklidir. Eski çalışma zamanının hedefini kullanıyorsanız, Unity için Visual Studio Araçları DLL ve PDB'den bilgileri kullanarak eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi olan DLL.MDB dosyasını oluşturur. Yeni çalışma zamanının hedefini kullanıyorsanız ve Taşınabilir PDB kullanıyorsanız, yeni Unity çalışma zamanı Taşınabilir PDB'leri yerel olarak kullanamayacagın Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmaya çalışmaz.

   PDB oluşturma hakkında daha fazla bilgi için buraya [bakın.](/debugger/how-to-set-debug-and-release-configurations.md) Yeni çalışma zamanının hedefini kullanıyorsanız, Taşınabilir PDB'nin düzgün bir şekilde oluşturularak "Hata Ayıklama Bilgileri"nin "Taşınabilir" olarak ayarlanmış olduğundan emin olun. Eski çalışma zamanının hedefini kullanıyorsanız "Tam" kullansanız iyi olur.

4. Kodunuzun hata ayıklaması. Artık UNITY projenizin kaynak koduyla birlikte DLL kaynak kodunuzun hatasını ayıkabilir ve kesme noktaları ve kodda adımlama gibi kullanılan tüm hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Klavye kısayollarını kullanarak unity Visual Studio hızlı bir şekilde erişebilirsiniz. Burada, kullanılabilen kısayolların özeti ve bulunmaktadır.

:::zone pivot="windows"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior Sihirbazı'nı açın|**Ctrl tuşunu basılı tutarak** + **Shift ile kaydırma** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Unity Project Explorer'ı açın|**Alt** + **Shift ile kaydırma** + **E**|**View.UnityProjectExplorer**|
|Unity belgelerine erişme|**Ctrl tuşunu basılı tutarak** + **Alt** + **M, Ctrl** + **H**|**Help.UnityAPIReference**|
|Unity hata ayıklayıcısına ekleme (oynatıcı veya düzenleyici)|**_varsayılan yok_**|**Debug.AttachUnityDebugger**|

Varsayılanı 100'den fazla 300'e kadar olan tüm kısayol tuş bileşimlerini değiştirebilirsiniz. Nasıl değiştirebileceğiniz hakkında bilgi için bkz. Visual Studio' içinde [klavye kısayollarını tanımlama ve özelleştirme.](/docs/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

:::zone-end
:::zone pivot="macos"

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior Sihirbazı'nı açın|**Cmd** + **Shift ile kaydırma** + **M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Unity belgelerine erişme|**Cmd+'**|**Help.UnityAPIReference**|

Varsayılanı 100'den fazla 300'e kadar olan tüm kısayol tuş bileşimlerini değiştirebilirsiniz. Bunu değiştirme hakkında bilgi için bkz. [IDE'i Özelleştirme.](/mac/customizing-the-ide#key-bingings)

:::zone-end

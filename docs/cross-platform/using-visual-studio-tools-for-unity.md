---
title: Unity için Visual Studio Araçları kullanma | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f65945f28a577201c1308694bb7196d464330dc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815168"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio 'da Unity betikleri açın

[Unity için dış betik düzenleyicisi olarak](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)Visual Studio ayarlandığında, Unity düzenleyiciden herhangi bir betiği açmak, seçilen komut dosyası açılarak otomatik olarak Visual Studio 'yu başlatır veya bu şekilde geçiş yapar. Unity projenizde bir betiğe çift tıklayın.

Alternatif olarak, Unity 'de **varlıklar** menüsünden **C# projesi aç** ' ı seçerek Visual Studio 'yu, kaynak düzenleyicide açık betik olmadan açabilirsiniz.

![C# projesini aç](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Unity belge erişimi

Unity betik belgelerine Visual Studio 'dan hızlıca erişebilirsiniz. API belgelerini yerel olarak bulamazsa Unity için Visual Studio Araçları çevrimiçi bulmaya çalışır.

- Visual Studio 'da imleci, hakkında bilgi edinmek istediğiniz Unity API 'sinin üzerine getirin veya yerleştirin, sonra **CTRL** + **alt** + **M**, **CTRL** + **H** tuşlarına basın

## <a name="intellisense-for-unity-api-messages"></a>Unity API Iletileri için IntelliSense

IntelliSense kod tamamlama, tek davranış betiklerine Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API 'sini öğrenmeye yardımcı olur. Unity iletileri için IntelliSense 'i kullanmak için:

1. İmleci, ' den türetilen bir sınıfın gövdesinin içine yeni bir satıra yerleştirin `MonoBehaviour` .

2. Bir Unity iletisinin adını yazmaya başlayın, örneğin `OnTriggerEnter` .

3. "**Ontri**" harfleri yazıldıktan sonra, bir IntelliSense önerisi listesi görüntülenir.

   ![IntelliSense Kullanma](media/vstu_intellisense1.png)

4. Listedeki seçim üç şekilde değiştirilebilir:

    - **Yukarı** ve **aşağı** ok tuşlarıyla.

    - İstenen öğenin üzerine fareyle tıklanarak.

    - İstenen öğenin adını yazmaya devam edin.

5. IntelliSense, gerekli parametreler dahil olmak üzere seçili Unity iletisini ekleyebilir:

    - **Sekmesine**basarak.

    - **ENTER**tuşuna basarak.

    - Seçili öğeye çift tıklayarak.

   ![IntelliSense 'den Unity iletisi Ekle](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior betik Sihirbazı

Tek davranış Sihirbazı ' nı kullanarak tüm Unity API yöntemlerinin bir listesini görüntüleyebilir ve boş bir tanımı hızlıca uygulayabilirsiniz. Bu özellik özellikle, **Yöntem açıklamalarını oluştur** seçeneği etkinken, Unity API 'sinde nelerin kullanılabildiğini öğrenseniz yararlı olur.

MonoBehavior sihirbazıyla boş MonoBehavior yöntemi tanımları oluşturmak için:

1. Visual Studio 'da yöntemlerin eklenmesini istediğiniz yere konumlandırın, sonra **Ctrl** + **Shift** + MonoBehavior sihirbazını başlatmak için CTRL SHIFT**e** tuşlarına basın.

2. **Betik yöntemleri oluştur** penceresinde, eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü seçmek için **Framework sürümü** açılan listesini kullanın.

4. Varsayılan olarak, Yöntemler İmlecin konumuna eklenir. Alternatif olarak, **ekleme noktası** açılır listesinin değerini istediğiniz konuma değiştirerek, sınıfınıza zaten uygulanmış herhangi bir yöntemden sonra bunları eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemlere yorum oluşturmasını istiyorsanız, **Yöntem açıklamaları oluştur** onay kutusunu işaretleyin. Bu yorumlar, yöntemin ne zaman çağrıldığını ve genel sorumlulukların ne zaman olduğunu anlamanıza yardımcı olmak için tasarlanmıştır.

6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.

   ![MonoBehavior Sihirbazı iletişim kutusu.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Unity Proje Gezgini

![Unity Proje Gezgini penceresi.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Proje Gezgini tüm Unity proje dosyalarınızı ve dizinlerinizi Unity düzenleyiciyle aynı şekilde gösterir. Bu, Unity betiklerinizde, bunları projeler ve Visual Studio tarafından oluşturulan bir çözüme düzenleyen normal Visual Studio Çözüm Gezgini ile gezinmeden farklıdır.

- Ana Visual Studio menüsünde **görünüm > Unity Proje Gezgini**' ni seçin. Klavye kısayolu: **alt** + **Shift** + **E**

   ![Unity Proje Gezgini penceresini görüntüleyin.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Unity hata ayıklaması

Unity için Visual Studio Araçları, Visual Studio 'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için hem Düzenleyici hem de oyun betiklerinin hatalarını ayıklamanızı sağlar.

### <a name="debug-in-the-unity-editor"></a>Unity düzenleyicisinde hata ayıklama

#### <a name="start-debugging"></a>Hata ayıklamayı Başlat

1. **Unity 'ye Ekle**etiketli **oynat** düğmesine tıklayarak ve **F5**klavye kısayolunu kullanarak Visual Studio 'yu Unity 'ye bağlayın.

   ![Visual Studio 'da Yürüt ' e tıklayın](media/vstu_play-button.png)

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.

   ![Unity 'de Yürüt ' e tıklayın](media/vstu_unity-play-button.png)

3. Oyun, Visual Studio 'ya bağlıyken Unity Düzenleyicisi 'nde çalışırken, karşılaştığı herhangi bir kesme noktası oyunun yürütülmesini duraklatır ve oyunun Visual Studio 'daki kesme noktasına isabet ettiği kod satırını getirir.

#### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

- Visual Studio 'da **Durdur** düğmesine tıklayın veya klavye kısayolunun **SHIFT + F5**tuşlarını kullanın.

  ![Visual Studio 'da Durdur ' a tıklayın](media/vstu_stop-debugger.png)

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Unity 'ye Ekle ve Yürüt

Ek kolaylık sağlamak için Unity 'ye **Ekle** düğmesini, **Unity ve Play moduna eklemek** için değiştirebilirsiniz.

1. **Unity 'ye Ekle** düğmesinin yanındaki küçük **aşağı oka** tıklayın.

1. **Unity 'ye Ekle ve açılır menüden Oynat ' ı** seçin.

    ![Ekle ve çal](media/vstu_attach-and-play.png)

Oynat düğmesi, **Unity 'ye Ekle ve Yürüt**şeklinde etiketlenmiş hale gelir. Bu düğmeye tıkladığınızda veya klavye kısayolunun **F5** 'i kullanmak artık Unity düzenleyicisine otomatik olarak geçer ve Visual Studio hata ayıklayıcıyı eklemenin yanı sıra oyunu düzenleyicide çalıştırır.

Visual Studio 'daki **Durdur** düğmesine tıklamak veya klavye kısayolunun **SHIFT tuşlarını**kullanmak, + **F5** Unity düzenleyicisinde oyunu otomatik olarak durdurur.

### <a name="debug-unity-player-builds"></a>Unity oynatıcı Derlemeleriyle hata ayıkla

Visual Studio ile çeşitli Unity oynatıcıların geliştirme Derlemeleriyle ilgili hata ayıklaması yapabilirsiniz.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity Player 'da betik hata ayıklamasını etkinleştirme

1. Unity 'de **dosya > yapı ayarları**' nı seçerek yapı ayarlarını açın.

2. Derleme ayarları penceresinde, **geliştirme derlemesi** ve **betik hata ayıklama** onay kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı iliştirmek için bir Unity örneği seçin

- Visual Studio 'da, ana menüdeki **hata ayıkla > Unity hata ayıklayıcı Ekle**' yi seçin.

   ![Unity hata ayıklayıcısını iliştirin.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity örneği Seç** iletişim kutusu, bağlandığınız her Unity örneğiyle ilgili bazı bilgileri görüntüler.

   ![Bağlanılacak Unity örneğini seçin.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Unity 'nin bu örneğinde çalışan Unity projesinin adı.

   **Makine** Bu Unity örneğinin üzerinde çalıştığı bilgisayarın veya cihazın adı.

   Unity 'in bu örneği Unity Düzenleyicisi 'nin bir parçası olarak çalışıyorsa, **tür** **Düzenleyici** ; Bu Unity örneği tek başına bir oynatıcı ise **oynatıcı** .

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Unity için Visual Studio Araçları ve Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınız hakkında sorun olabilir. Bu durumda, VSTU ve Unity 'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizde DLL hatalarını ayıklama

Birçok Unity geliştiricisi, geliştirme işlevlerinin diğer projelerle kolayca paylaşılması için kod bileşenlerini dış dll 'Ler olarak yazıyor. Unity için Visual Studio Araçları, bu DLL 'Lerdeki kodun, Unity projenizdeki diğer kodla sorunsuz bir şekilde ayıklanabilmesini kolaylaştırır.

> [!NOTE]
> Şu anda Unity için Visual Studio Araçları yalnızca yönetilen DLL 'Leri destekler. C++ dilinde yazılmış olanlar gibi yerel kod dll 'Lerinde hata ayıklamayı desteklemez.

Burada açıklanan senaryo kaynak koda sahip olduğunuzu varsayar. Yani, kendi birinci taraf kodunuzu geliştirdiğinizi veya yeniden kullandığınızı veya bir üçüncü taraf kitaplığına kaynak kodu kullandığınızı ve bunu bir DLL olarak Unity projenizde dağıtmayı planladığınızı unutmayın. Bu senaryo, kaynak kodu olmayan bir DLL 'nin hata ayıklamasını tanımlamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan bir yönetilen DLL projesinde hata ayıklamak için

1. Mevcut DLL projenizi Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümüne ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenleri içeren yeni bir yönetilen DLL projesi başlatıyorsunuz olabilirsiniz; Bu durumda, bunun yerine Visual Studio çözümüne yeni bir yönetilen DLL projesi ekleyebilirsiniz. Bir çözüme yeni veya var olan bir proje ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir çözüme proje ekleme](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Varolan DLL projenizi çözüme ekleyin.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   Her iki Unity için Visual Studio Araçları durumda da, proje başvurusunu ve çözüm dosyalarını yeniden oluşturmak zorunda olsa bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity Framework profiline başvurun. Visual Studio 'da, DLL projesinin özelliklerinde, **hedef Framework** özelliğini kullandığınız Unity çerçevesi sürümü olarak ayarlayın. Bu, projenizin hedeflediği, Unity Full, mikro veya Web temel sınıf kitaplıkları gibi API uyumluluğuyla eşleşen Unity temel sınıf kitaplığıdır. Bu, DLL 'nizin diğer çerçeveler veya uyumluluk düzeylerinde bulunan ancak kullanmakta olduğunuz Unity çerçevesi sürümünde mevcut olmayan çerçeve yöntemlerini aramasını engeller.

> [!NOTE]
> Yalnızca Unity 'nin eski çalışma zamanını kullanıyorsanız, şunlar gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, bu adanmış 3,5 profillerini artık kullanmanız gerekmez. Unity sürümünüz ile uyumlu bir .NET 4. x profili kullanın.

   ![DLL 'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. DLL 'yi Unity projenizin varlık klasörüne kopyalayın. Unity 'de varlıklar, çalışma zamanında yüklenebilmeleri için paketlenmiş ve Unity uygulamanız ile birlikte dağıtılan dosyalardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık olarak dağıtılması için Unity Düzenleyicisi, dll 'Lerin Unity projenizdeki varlıklar klasörünün içine yerleştirilmesi gerekir. Bunu iki şekilde yapabilirsiniz:

   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.

   DLL 'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kodu formuyla eşlediklerinden, PDB dosyaları hata ayıklama için gereklidir. Eski çalışma zamanını hedefliyorsanız, Unity için Visual Studio Araçları dll ve PDB 'den DLL oluşturmak için bu bilgileri kullanır. MDB dosyası, eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembolü biçimidir. Yeni bir çalışma zamanını hedefliyorsanız ve taşınabilir-PDB kullanıyorsanız, yeni Unity çalışma zamanı yerel olarak taşınabilir-pdb 'leri tüketebileceği için Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmayı denemeyecektir.

   PDB oluşturma hakkında daha fazla bilgiyi [burada](../debugger/how-to-set-debug-and-release-configurations.md)bulabilirsiniz. Yeni çalışma zamanını hedefliyorsanız, taşınabilir-PDB ' yi düzgün bir şekilde oluşturmak için "hata ayıklama bilgileri" ın "taşınabilir" olarak ayarlandığından emin olun. Eski çalışma zamanını hedefliyorsanız, "Full" kullanmanız gerekir.

4. Kodunuzda hata ayıklayın. Artık DLL kaynak kodunuzda, Unity projenizin kaynak kodu ile birlikte hata ayıklama yapabilir ve kesme noktaları ve kod üzerinden atlama gibi tüm hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio işlevselliği için Unity araçlarına, klavye kısayollarını kullanarak hızlıca erişebilirsiniz. Mevcut kısayolların özeti aşağıda verilmiştir.

|Komut|Kısayol|Kısayol komutu adı|
|-------------|--------------|---------------------------|
|MonoBehavior sihirbazını açın|**CTRL** + **SHIFT** + **A**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity proje Gezginini açın|**Alt** + **SHIFT** + **E**|**View. Unityprojecbir**|
|Unity belgelerine erişin|**CTRL** + **Alt** + **A, CTRL** + **H**|**Help. UnityAPIReference**|
|Unity hata ayıklayıcıya (oynatıcı veya düzenleyici) iliştirme|**_Varsayılan değer yok_**|**Debug. AttachUnityDebugger**|

Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio 'da klavye kısayollarını belirleme ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

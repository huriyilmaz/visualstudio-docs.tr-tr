---
title: Birlik için Visual Studio Araçlarını Kullanma | Microsoft Dokümanlar
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5a0595fdf7331c8b2825c6092b5b29a19974887b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302261"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde, Unity'nin tümleştirme ve üretkenlik özellikleri için Visual Studio Araçlarını nasıl kullanacağınızı ve Unity geliştirme için Visual Studio hata ayıklamaaracının nasıl kullanılacağını öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio'da Unity komut dosyalarını açın

Visual Studio [Unity için dış komut dosyası editörü olarak ayarlandıktan](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)sonra, Unity editöründen herhangi bir komut dosyası nın açılması otomatik olarak başlatılır veya seçilen komut dosyası açık ken Visual Studio'ya geçer. Unity projenizde bir komut dosyasına çift tıklamanız yeterlidir.

Alternatif olarak, Unity'deki **Varlıklar** menüsünden **Açık C# Project'i** seçerek kaynak düzenleyicide komut dosyası açık olmayan Visual Studio'yu açabilirsiniz.

![C# projesini aç](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Birlik belgelerine erişim

Unity komut dosyası belgelerine Visual Studio'dan hızlı bir şekilde erişebilirsiniz. Visual Studio Tools for Unity API belgelerini yerel olarak bulamazsa, çevrimiçi olarak bulmaya çalışır.

- Visual Studio'da imleci öğrenmek istediğiniz Unity API'nin üzerine vurgulayın veya yerleştirin, ardından **Ctrl**+**Alt**+**M**, **Ctrl**+**H** tuşlarına basın

## <a name="intellisense-for-unity-api-messages"></a>Birlik API Mesajları için Intellisense

Intellisense kod tamamlama, MonoBehaviour komut dosyasında Unity API iletilerinin uygulanmasını kolaylaştırır ve Unity API'yi öğrenmede yardımcı olur. Birlik mesajları için IntelliSense'i kullanmak için:

1. İmleci, türetilen bir sınıfın gövdesi içinde yeni `MonoBehaviour`bir çizgiüzerine yerleştirin.

2. Birleşme iletisinin adını yazmaya baÅ `OnTriggerEnter`lat

3. "**ontri**" harfleri yazıldıktan sonra IntelliSense önerilerinin bir listesi görüntülenir.

   ![IntelliSense Kullanma](media/vstu_intellisense1.png)

4. Listedeki seçim üç şekilde değiştirilebilir:

    - **Yukarı** ve **Aşağı** ok tuşları ile.

    - İstenilen öğenin üzerinde fare ile tıklayarak.

    - İstenilen öğenin adını yazmaya devam ederek.

5. IntelliSense, gerekli parametreler de dahil olmak üzere seçili Birlik iletisini ekleyebilir:

    - **Sekme tuşuna**basarak .

    - **Enter**tuşuna basarak .

    - Seçili öğeyi çift tıklatarak.

   ![IntelliSense'den Birlik iletisi ekleme](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior komut dosyası sihirbazı

Tüm Unity API yöntemlerinin listesini görüntülemek ve boş bir tanımı hızla uygulamak için MonoBehavior sihirbazını kullanabilirsiniz. Bu özellik, özellikle Oluşturma **yöntemi açıklamaları** seçeneği etkinken, Unity API'de nelerin mevcut olduğunu hala öğreniyorsanız yararlıdır.

MonoBehavior sihirbazı ile boş MonoBehavior yöntem tanımları oluşturmak için:

1. Visual Studio'da imleci yöntemlerin eklenmesini istediğiniz yere yerleştirin ve MonoBehavior sihirbazını başlatmak için **Ctrl**+**Shift**+**M** tuşuna basın.

2. Komut **dosyası oluşturma yöntemleri** penceresinde, eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü seçmek için **Framework sürüm** açılır dosyasını kullanın.

4. Varsayılan olarak, yöntemler imlecin konumuna eklenir. Alternatif olarak, **Ekleme noktası** açılır değerini istediğiniz konuma değiştirerek sınıfınızda zaten uygulanmış herhangi bir yöntemden sonra eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemler için açıklama oluşturmasını istiyorsanız, **oluşturma yöntemi açıklamaları** onay kutusunu işaretleyin. Bu yorumlar, yöntemin ne zaman çağrıldığını ve genel sorumluluklarının ne olduğunu anlamanıza yardımcı olmak içindir.

6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.

   ![Monobehavior sihirbazı iletişim kutusu.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Birlik Proje Explorer

![Birlik Projesi Gezgini penceresi.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Project Explorer, tüm Unity proje dosyalarınızı ve dizinlerinizi Unity Düzenleyicisi ile aynı şekilde gösterir. Bu, unity komut dosyalarınızda, onları projelere ve Visual Studio tarafından oluşturulan bir çözüme düzenleyen normal Visual Studio Solution Explorer ile gezinmekten farklıdır.

- Ana Visual Studio **menüsünde, Unity Project Explorer>** görüntüleyin'i seçin. Klavye kısayolu: **Alt**+**Shift**+**E**

   ![Birlik Projesi Gezgini penceresini görüntüleyin.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Birlik hata ayıklama

Visual Studio Tools for Unity, Visual Studio'nun güçlü hata ayıklama aracını kullanarak Unity projeniz için hem editör hem de oyun komut hatalarını ayıklamanızı sağlar.

### <a name="debug-in-the-unity-editor"></a>Unity editöründe hata ayıklama

#### <a name="start-debugging"></a>Hata ayıklama yı başlatma

1. **Birliğe Ekle**etiketli **Oynat** düğmesini tıklatarak Visual Studio'yu Birliğe Bağlayın veya Klavye kısayolu **F5'i**kullanın.

   ![Visual Studio'da Oynat'a tıklayın](media/vstu_play-button.png)

2. Unity'ye geçin ve oyunu editörde çalıştırmak için **Play** butonuna tıklayın.

   ![Unity Oyna'ya tıklayın](media/vstu_unity-play-button.png)

3. Visual Studio'ya bağlıyken unity editöründe oyun çalışırken, karşılaşılan herhangi bir kesme noktası oyunun yürütülmesini duraklatacak ve oyunun Visual Studio'da kırılma noktasına geldiği kod çizgisini açacaktır.

#### <a name="stop-debugging"></a>Hata ayıklamayı durdur

- Visual Studio'da **Durdur** düğmesini tıklatın veya klavye kısayolu **Shift + F5'i**kullanın.

  ![Visual Studio'da Dur'a tıklayın](media/vstu_stop-debugger.png)

Visual Studio'da hata ayıklama hakkında daha fazla bilgi edinmek için [Visual Studio Debugger'a ilk bakışbölümüne bakın.](../debugger/debugger-feature-tour.md)

#### <a name="attach-to-unity-and-play"></a>Birlik ve Oyun Ekle

Daha fazla kolaylık sağlamak **için, Birliğe Ekle** **ve Oynatma moduna ekle düğmesini** değiştirebilirsiniz.

1. Unity düğmesine ekle düğmesinin yanındaki küçük **aşağı** **ok'u** tıklatın.

1. Açılan menüden **Unity ve Play'e Ekle'yi** seçin.

    ![Ekle ve oyna](media/vstu_attach-and-play.png)

Oynat düğmesi **Unity ve Play'e ekle**etiketine dönüşür. Bu düğmeyi tıklatarak veya klavye kısayolu **F5** kullanarak artık otomatik olarak Unity düzenleyiciye geçer ve Visual Studio hata ayıklayıcı eklemeye ek olarak, editör de oyunu çalıştırın.

Visual Studio'da **Durdur** düğmesine veya klavye kısayolu **Shift**+**F5'i** tıklatarak Unity editöründeki oyunu otomatik olarak durdurur.

### <a name="debug-unity-player-builds"></a>Hata Ayıklama Unity oyuncu oluşturur

Visual Studio ile çeşitli Unity oyuncularının geliştirme yapılarını hata ayıklayabilirsiniz.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity player'da komut dosyası hata ayıklamasını etkinleştirme

1. Unity'de, Yapı Ayarları > Dosya'yı seçerek Yapı **Ayarları'nı**açın.

2. Yapı Ayarları penceresinde, **Geliştirme Yapısı** ve Komut Dosyası Hata Ayıklama onay kutularını **işaretleyin.**

   ![Hata ayıklama için Unity yapı ayarlarını yapılandırın.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklama aracını eklemek için bir Birlik örneği seçin

- Visual Studio'da, ana menüde **Hata Ayıklama > Unity Debugger'ı takın'ı**seçin.

   ![Birlik hata ayıklama sını takın.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Birlik Örneği Seç** iletişim kutusu bağlanabileceğiniz her Birlik örneği hakkında bazı bilgiler görüntüler.

   ![Bağlanmak için Birlik'in bir örneğini seçin.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Proje**

   Bu Birlik örneğinde çalışan Birlik projesinin adı.

   **Makine** Bu Unity örneğinin üzerinde çalıştırdığı bilgisayarın veya aygıtın adı.

   Bu Unity örneği Unity Editor'un bir parçası olarak çalışıyorsa, **Editör** **yazın;** **Oyuncu** Birlik bu örnek tek başına bir oyuncu ise.

   **Bağlantı Noktası** Bu Unity örneğinin iletişim halinde olduğu UDP soketinin bağlantı noktası numarası.

> [!IMPORTANT]
> Visual Studio Tools for Unity ve Unity örneği bir UDP ağ soketi üzerinden iletişim kurun, güvenlik duvarınız bu konuda soru sorabilir. Bu durumda, VSTU ve Unity'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.

### <a name="debug-a-dll-in-your-unity-project"></a>Birlik projenizde bir DLL hata ayıklama

Birçok Unity geliştiricisi, geliştirdikleri işlevselliğin diğer projelerle kolayca paylaşılabilmeleri için kod bileşenlerini harici DL'ler olarak yazıyor. Visual Studio Tools for Unity, Unity projenizdeki diğer kodlarla birlikte bu DL'lerde kod ayıklamanızı kolaylaştırır.

> [!NOTE]
> Şu anda Visual Studio Tools for Unity yalnızca yönetilen DL'leri destekler. C++'da yazılmış olanlar gibi yerel kod DL'lerinin hata ayıklamalarını desteklemez.

Burada açıklanan senaryonun kaynak koduna sahip olduğunuzu varsayıldığını, yani kendi birinci taraf kodunuzu geliştirdiğinizi veya yeniden kullandığınızı veya kaynak kodunu bir üçüncü taraf kitaplığına sahip olduğunuzu ve bunu Birlik projenizde DLL olarak dağıtmayı planladığınızı unutmayın. Bu senaryo, kaynak koduna sahip olmadığınız bir DLL hata ayıklama açıklamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan yönetilen bir DLL projesini hata ayıklamak için

1. Visual Studio Tools for Unity tarafından oluşturulan Visual Studio çözümüne mevcut DLL projenizi ekleyin. Daha az yaygın olarak, Birlik projenizde kod bileşenlerini içerecek şekilde yeni yönetilen bir DLL projesi başlatmış olabilirsiniz; bu durumda, Visual Studio çözümüne yeni yönetilen bir DLL projesi ekleyebilirsiniz. Bir çözüme yeni veya varolan bir proje ekleme hakkında daha fazla bilgi için [bkz.](https://msdn.microsoft.com/library/ff460187.aspx)

   ![Mevcut DLL projenizi çözüme ekleyin.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   Her iki durumda da, Visual Studio Tools for Unity proje başvurusunu korur, proje ve çözüm dosyalarını yeniden oluşturması gerekse bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.

2. DLL projesinde doğru Unity çerçeve profiline başvurun. Visual Studio'da, DLL projesinin özelliklerinde Hedef **çerçeve** özelliğini kullanmakta olduğunuz Unity framework sürümüne ayarlayın. Bu, Projenizin tam, mikro veya web tabanı sınıf kitaplıkları gibi hedeflenebilen API uyumluluğuyla eşleşen Unity Base Class Kitaplığıdır. Bu, DLL'nizin diğer çerçevelerde veya uyumluluk düzeylerinde var olan ancak kullanmakta olduğunuz Unity framework sürümünde bulunmayan çerçeve yöntemlerini aramasını engeller.

> [!NOTE]
> Aşağıdakiler yalnızca Unity'nin eski çalışma süresini kullanıyorsanız gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, artık bu özel 3,5 profillerini kullanmanız gerekmez. Unity sürümünüzle uyumlu bir .NET 4.x profili kullanın.

   ![DLL'nin hedef çerçevesini Birlik çerçevesine ayarlayın.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. DLL'yi Unity projenizin Varlık klasörüne kopyalayın. Unity'de varlıklar, unity uygulamanızla birlikte paketlenen ve dağıtılan dosyalardır, böylece bunlar çalışma zamanında yüklenebilir. DL'ler çalışma zamanında bağlandığından, DL'lerin varlık olarak dağıtılması gerekir. Bir varlık olarak dağıtılmak için, Unity Düzenleyicis'in Unity projenizdeki Varlıklar klasörüne DL'lerin koymasını gerektirir. Bunu yapmanın iki yolu vardır:

   - DLL projenizin yapı ayarlarını, çıktı klasöründen Unity projenizin **Varlıklar** klasörüne çıktı DLL ve PDB dosyalarını kopyalayan bir görev içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **Varlıklar** klasörü olarak ayarlamak için DLL projenizin yapı ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **Varlıklar** klasörüne yerleştirilir.

   DLL'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kod formuyla eşledikleri için PDB dosyaları hata ayıklama için gereklidir. Eski çalışma süresini hedefliyorsanız, Visual Studio Tools for Unity bir DLL oluşturmak için DLL ve PDB'den gelen bilgileri kullanır. MDB dosyası, eski Unity komut dosyası altyapısı tarafından kullanılan hata ayıklama sembolü biçimidir. Yeni çalışma süresini hedefliyorsanız ve Portable-PDB kullanıyorsanız, Yeni Unity çalışma zamanı Taşınabilir PDB'leri yerel olarak tüketebildiği için Visual Studio Tools for Unity herhangi bir sembol dönüştürme yapmaya çalışmaz.

   PDB üretimi hakkında daha fazla bilgiyi [burada](/visualstudio/debugger/how-to-set-debug-and-release-configurations)bulabilirsiniz. Yeni çalışma süresini hedefliyorsanız, portable-PDB'yi düzgün bir şekilde oluşturmak için lütfen "Hata Ayıklama Bilgileri"nin "Taşınabilir" olarak ayarlandıklarına emin olun. Eski çalışma süresini hedefliyorsanız, "Tam" kullanmanız gerekir.

4. Kodunuzu hata ayıklamak. Artık DLL kaynak kodunuzu Unity projenizin kaynak koduyla birlikte hata ayıklayabilir ve kesme noktaları ve kod üzerinden geçiş gibi alışık olduğunuz tüm hata ayıklama özelliklerini kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Klavye kısayollarını kullanarak Visual Studio için Birlik Araçları işlevine hızla erişebilirsiniz. Burada kullanılabilen kısayolların bir özeti verem.

|Komut|Kısayol|Kısayol komut adı|
|-------------|--------------|---------------------------|
|MonoBehavior Sihirbazı'nı aç|**Ctrl**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Birlik Projesi Gezgini'ni açın|**Alt**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Access Unity belgelerine|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Unity hata ayıklayıcıya (oyuncu veya editör) ekle|**_varsayılan yok_**|**Debug.AttachUnityDebugger**|

Varsayılanı beğenmezseniz kısayol tuşu birleşimlerini değiştirebilirsiniz. Nasıl değiştireceğiniz hakkında bilgi için [Visual Studio'daki klavye kısayollarını tanımla ve özelleştir'e](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)bakın.

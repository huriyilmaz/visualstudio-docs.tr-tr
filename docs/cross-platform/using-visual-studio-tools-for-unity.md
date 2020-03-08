---
title: Unity için Visual Studio araçlarını kullanma | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408794"
---
# <a name="use-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları’nı Kullanma

Bu bölümde, Visual Studio Araçları Unity'nın tümleştirme ve verimlilik özellikleri için nasıl kullanılacağını ve Unity'de geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio'da Unity betikleri açma

[Unity için dış betik düzenleyicisi olarak](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)Visual Studio ayarlandığında, Unity düzenleyiciden herhangi bir betiği açmak, seçilen komut dosyası açılarak otomatik olarak Visual Studio 'yu başlatır veya bu şekilde geçiş yapar. Yalnızca bir betik Unity projenizde çift tıklayın.

Alternatif olarak, Unity 'de **varlıklar** menüsünden **Proje Aç C#**  ' ı seçerek Visual Studio 'yu, kaynak düzenleyicide açık betik olmadan açabilirsiniz.

![C# proje Aç](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Unity belgeleri erişimi

Unity betik belgelerine Visual Studio'dan hemen erişebilir. Unity için Visual Studio Araçları, yerel olarak API belgeleri bulamazsa, çevrimiçi bulmayı deneyecek.

- Visual Studio 'da, imleci hakkında bilgi edinmek istediğiniz Unity API 'sinin üzerine getirin veya yerleştirin, sonra **ctrl**+**alt**+**M**, **CTRL**+**H** tuşlarına basın

## <a name="intellisense-for-unity-api-messages"></a>API Unity iletileri için IntelliSense

IntelliSense kod tamamlama, MonoBehaviour betiklerde API Unity iletilerini Uygula kolaylaştırır ve Unity API öğrenmeye yardımcı olur. Unity iletileri için IntelliSense kullanmak için:

1. İmleci, `MonoBehaviour`türetilen bir sınıf gövdesinin içine yeni bir satıra yerleştirin.

2. `OnTriggerEnter`gibi bir Unity iletisinin adını yazmaya başlayın.

3. "**Ontri**" harfleri yazıldıktan sonra, bir IntelliSense önerisi listesi görüntülenir.

   ![IntelliSense Kullanma](media/vstu_intellisense1.png)

4. Seçim listesindeki üç yolla değiştirilebilir:

    - **Yukarı** ve **aşağı** ok tuşlarıyla.

    - İstenen öğe üzerinde fare ile tıklayarak.

    - İstenen öğe adı devam ederek.

5. IntelliSense, tüm gerekli parametreleri de dahil olmak üzere seçili Unity ileti ekleyebilirsiniz:

    - **Sekmesine**basarak.

    - **ENTER**tuşuna basarak.

    - Seçili öğeyi çift tıklayarak.

   ![Unity iletisi IntelliSense'de Ekle](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior komut dosyası Sihirbazı

Unity API yöntemlerin listesini görüntülemek ve hızlı bir şekilde boş bir tanım uygulamak için MonoBehavior Sihirbazı'nı kullanabilirsiniz. Bu özellik özellikle, **Yöntem açıklamalarını oluştur** seçeneği etkinken, Unity API 'sinde nelerin kullanılabildiğini öğrenseniz yararlı olur.

Boş MonoBehavior yöntemi tanımları MonoBehavior Sihirbazı'nı kullanarak oluşturmak için:

1. Visual Studio 'da, işaretçiyi yöntemlerin eklenmesini istediğiniz yere konumlandırın, sonra MonoBehavior sihirbazını başlatmak için **Ctrl**+**SHIFT**+**e** tuşlarına basın.

2. **Betik yöntemleri oluştur** penceresinde, eklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.

3. İstediğiniz sürümü seçmek için **Framework sürümü** açılan listesini kullanın.

4. Varsayılan olarak, yöntemleri imleç konuma eklenir. Alternatif olarak, **ekleme noktası** açılır listesinin değerini istediğiniz konuma değiştirerek, sınıfınıza zaten uygulanmış herhangi bir yöntemden sonra bunları eklemeyi seçebilirsiniz.

5. Sihirbazın seçtiğiniz yöntemlere yorum oluşturmasını istiyorsanız, **Yöntem açıklamaları oluştur** onay kutusunu işaretleyin. Bu açıklamalar, yöntem zaman çağrılır ve genel sorumlulukları nelerdir anlamanıza yardımcı olması için yöneliktir.

6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.

   ![MonoBehavior Sihirbazı iletişim kutusu.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Unity Proje Gezgini

![Unity Proje Gezgini penceresi.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Proje Gezgini tüm, Unity proje dosyalarınızı ve dizinlerinizi, Unity Editor'ın yaptığı aynı şekilde gösterir. Bu, normal Visual Studio çözümü, projeleri ve Visual Studio tarafından oluşturulan bir çözüm halinde bunları düzenler Gezgini ile Unity betiklerinizde gezinmek daha farklıdır.

- Ana Visual Studio menüsünde **görünüm > Unity Proje Gezgini**' ni seçin. Klavye kısayolu: **Alt**+**SHIFT**+**E**

   ![Unity Proje Gezgini penceresini görüntüleyin.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Unity hata ayıklama

Unity için Visual Studio Araçları hem Düzenleyici hem de Visual Studio'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için oyun betikleri hatalarını ayıklamanıza olanak tanır.

### <a name="debug-in-the-unity-editor"></a>Unity Düzenleyicisi'nde hata ayıklama

#### <a name="start-debugging"></a>Hata Ayıklamayı Başlat

1. **Unity 'ye Ekle**etiketli **oynat** düğmesine tıklayarak ve **F5**klavye kısayolunu kullanarak Visual Studio 'yu Unity 'ye bağlayın.

   ![Visual Studio'da Yürüt'e tıklayın](media/vstu_play-button.png)

2. Unity 'ye geçin ve oyunu düzenleyicide çalıştırmak için **Yürüt** düğmesine tıklayın.

   ![Unity Yürüt'e tıklayın](media/vstu_unity-play-button.png)

3. Oyun bağlıyken, Visual Studio için Unity Düzenleyicisi'nde çalışırken karşılaşılan herhangi bir kesme noktası oyun yürütülmesini Duraklat ve burada oyun Visual Studio'da kesme noktası isabet kod satırının getirecek.

#### <a name="stop-debugging"></a>Hata ayıklamayı Durdur

- Visual Studio 'da **Durdur** düğmesine tıklayın veya klavye kısayolunun **SHIFT + F5**tuşlarını kullanın.

  ![Visual Studio'da Durdur'u tıklatın](media/vstu_stop-debugger.png)

Visual Studio 'da hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Unity ve Play ekleyin

Ek kolaylık sağlamak için Unity 'ye **Ekle** düğmesini, **Unity ve Play moduna eklemek** için değiştirebilirsiniz.

1. **Unity 'ye Ekle** düğmesinin yanındaki küçük **aşağı oka** tıklayın.

1. **Unity 'ye Ekle ve açılır menüden Oynat ' ı** seçin.

    ![Ekleme ve Yürüt](media/vstu_attach-and-play.png)

Oynat düğmesi, **Unity 'ye Ekle ve Yürüt**şeklinde etiketlenmiş hale gelir. Bu düğmeye tıkladığınızda veya klavye kısayolunun **F5** 'i kullanmak artık Unity düzenleyicisine otomatik olarak geçer ve Visual Studio hata ayıklayıcıyı eklemenin yanı sıra oyunu düzenleyicide çalıştırır.

Visual Studio 'daki **Durdur** düğmesine tıklamak veya klavye kısayol **kaydırma tuşlarını** kullanmak+**F5** , Unity düzenleyicisinde oyunu otomatik olarak durdurur.

### <a name="debug-unity-player-builds"></a>Hata ayıklama Unity Player'da derlemeleri

Visual Studio Unity oyuncularla çeşitli geliştirme derlemelerini ayıklayabilirsiniz.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity Player'da betik hata ayıklamasını etkinleştirme

1. Unity 'de **dosya > yapı ayarları**' nı seçerek yapı ayarlarını açın.

2. Derleme ayarları penceresinde, **geliştirme derlemesi** ve **betik hata ayıklama** onay kutularını işaretleyin.

   ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Hata ayıklayıcıyı iliştirmek için bir Unity örneği Seç

- Visual Studio 'da, ana menüdeki **hata ayıkla > Unity hata ayıklayıcı Ekle**' yi seçin.

   ![Unity hata ayıklayıcısını iliştirin.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity örneği Seç** iletişim kutusu, bağlandığınız her Unity örneğiyle ilgili bazı bilgileri görüntüler.

   ![Bağlanılacak Unity örneğini seçin.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Proje**

   Unity'nın bu örneğinde çalışan Unity proje adı.

   **Makine** Bu Unity örneğinin üzerinde çalıştığı bilgisayarın veya cihazın adı.

   Unity 'in bu örneği Unity Düzenleyicisi 'nin bir parçası olarak çalışıyorsa, **tür** **Düzenleyici** ; Bu Unity örneği tek başına bir oynatıcı ise **oynatıcı** .

   **Bağlantı noktası** Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.

> [!IMPORTANT]
> Unity ve Unity örneği için Visual Studio Araçları bir UDP ağ yuva iletişim kuran olduğundan, bu konuda, güvenlik duvarınızı isteyebilir. Böyle bir durumda VSTU ve Unity iletişim kurabilmesi için bağlantıyı yetkilendirmek zorunda kalırsınız.

### <a name="debug-a-dll-in-your-unity-project"></a>Unity projenizde bir DLL'nin hatasını ayıklayın

Geliştirme işlevleri diğer projeleri ile kolayca paylaşılabilir böylece birçok Unity geliştiricileri dış DLL'leri kod bileşenlerinin yazıyorsunuz. Unity için Visual Studio Araçları, Unity projenizdeki başka bir kod ile sorunsuz bir şekilde bu DLL'lerdeki kodun hatalarını ayıklamak kolaylaştırır.

> [!NOTE]
> Şu anda yalnızca destekler Unity için Visual Studio Araçları DLL'leri yönetilen. C++ ile yazılmış olanlar gibi DLL'leri, yerel kod hata ayıklamayı desteklemiyor.

Burada açıklanan senaryo kaynak kodu seçtiğinizi varsaydığını unutmayın; diğer bir deyişle, geliştirme veya kendi birinci taraf kodu yeniden kullanarak veya bir üçüncü taraf kitaplığına kod ve Unity projenizde bir DLL olarak dağıtmayı planladığınız kaynağı sahip. Bu senaryoda, kaynak kodu içermeyen bir DLL'nin hata ayıklama açıklamaz.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan yönetilen DLL projesinde hata ayıklamak için

1. Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümünü mevcut DLL projenize ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenlerini içerecek yeni bir yönetilen DLL proje başlatılıyor; Bu durumda, Visual Studio çözümüne yeni bir yönetilen DLL projesi bunun yerine ekleyebilirsiniz. Bir çözüme yeni veya var olan bir proje ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir çözüme proje ekleme](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Varolan DLL projenizi çözüme ekleyin.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   Böylece, yalnızca bir kez bu adımları gerçekleştirmek proje ve çözüm dosyaları yeniden yeniden oluşturmak olsa bile her iki durumda da, Unity için Visual Studio Araçları proje başvurusu tutar.

2. DLL projesi doğru Unity framework profilinde başvuru. Visual Studio 'da, DLL projesinin özelliklerinde, **hedef Framework** özelliğini kullandığınız Unity çerçevesi sürümü olarak ayarlayın. Unity temel sınıfı, Unity tam, mikro veya web gibi projenizin hedeflediği sınıf kitaplıklarını temel API uyumluluğuna eşleşen kitaplığı budur. Bu, DLL dosyanızı diğer çerçeveler ya da uyumluluk düzeyleri var, ancak kullandığınız Unity çerçeve sürümünde bulunmayabilir framework yöntemlerini çağırma engeller.

> [!NOTE]
> Yalnızca Unity 'nin eski çalışma zamanını kullanıyorsanız, şunlar gereklidir. Yeni Unity çalışma zamanını kullanıyorsanız, bu adanmış 3,5 profillerini artık kullanmanız gerekmez. Unity sürümünüz ile uyumlu bir .NET 4. x profili kullanın.

   ![DLL 'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. DLL Unity proje varlık klasörüne kopyalayın. Unity içinde paketlenir ve böylece kullanıcılar çalışma zamanında yüklenebilir Unity uygulamanız ile birlikte dağıtılan dosyaların varlıklardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık dağıtılması için Unity projenizde varlıklar klasörün içine yerleştirilecek DLL'leri Unity Editor gerektirir. Bunu yapmak için iki yolu vardır:

   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.

   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.

   PDB dosyaları, çünkü bunlar DLL'nin hata ayıklama sembolleri içeren ve kaynak kod hâli DLL kod eşleme hata ayıklama için gereklidir. Eski çalışma zamanını hedefliyorsanız, Unity için Visual Studio Araçları dll ve PDB 'den DLL oluşturmak için bu bilgileri kullanır. MDB dosyası, eski Unity betik altyapısı tarafından kullanılan hata ayıklama sembolü biçimidir. Yeni bir çalışma zamanını hedefliyorsanız ve taşınabilir-PDB kullanıyorsanız, yeni Unity çalışma zamanı yerel olarak taşınabilir-pdb 'leri tüketebileceği için Unity için Visual Studio Araçları herhangi bir sembol dönüştürmesi yapmayı denemeyecektir.

   PDB oluşturma hakkında daha fazla bilgiyi [burada](/visualstudio/debugger/how-to-set-debug-and-release-configurations)bulabilirsiniz. Yeni çalışma zamanını hedefliyorsanız, taşınabilir-PDB ' yi düzgün bir şekilde oluşturmak için "hata ayıklama bilgileri" ın "taşınabilir" olarak ayarlandığından emin olun. Eski çalışma zamanını hedefliyorsanız, "Full" kullanmanız gerekir.

4. Kodunuzdaki hataları ayıklamanıza. Artık, hata ayıklama DLL kaynak kodunuzu birlikte Unity projenizin kaynak kodunu ve tüm hata ayıklama özellikleri gibi kesme noktaları için kullanılır ve kod içerisinde ilerlemeye kullanabilirsiniz.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio işlevselliği için Unity araçları, klavye kısayollarını kullanarak hızlı şekilde erişebilirsiniz. Kullanılabilir kısayolları bir özeti aşağıda verilmiştir.

|Komut|Kısayol|Kısayol komut adı|
|-------------|--------------|---------------------------|
|MonoBehavior Sihirbazı'nı açın|**Ctrl**+**SHIFT**+**a**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Unity proje Gezgini'ni açın|**Alt**++**E** **Kaydır**|**View. Unityprojecbir**|
|Unity belgeleri erişimi|**Ctrl**+**alt**+**M, CTRL**+**H**|**Help. UnityAPIReference**|
|Unity (oynatıcı veya düzenleyici) hata ayıklayıcının|**_Varsayılan değer yok_**|**Debug. AttachUnityDebugger**|

Varsayılan beğenmezseniz kısayol tuş birleşimleri değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio 'da klavye kısayollarını belirleme ve özelleştirme](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

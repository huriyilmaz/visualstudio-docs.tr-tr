---
title: Unity için Visual Studio Araçları kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: cd05f5ebad1a07e818e377b90aeb5e137f296cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810289"
---
# <a name="using-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçlarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde Unity için Visual Studio Araçları tümleştirme ve üretkenlik özelliklerini kullanmayı ve Unity geliştirme için Visual Studio hata ayıklayıcısını kullanmayı öğreneceksiniz.  
  
## <a name="unity-integration-and-productivity"></a>Unity tümleştirmesi ve üretkenlik  
 Unity için Visual Studio Araçları, daha üretken olmanıza yardımcı olması için Unity Düzenleyicisi ile tümleşir. Bu üretkenlik geliştirme özellikleri, ortak betik görevlerinin otomatikleştirilmesi ve Unity 'den Visual Studio 'ya geçiş yaparken, bu bilgileri bulmak için Unity düzenleyicisine geçmeniz gerekmez.  
  
### <a name="unity-documentation-access"></a>Unity belge erişimi  
 Unity betik belgelerine Visual Studio 'dan hızlıca erişebilirsiniz. API belgelerini yerel olarak bulamazsa Unity için Visual Studio Araçları çevrimiçi bulmaya çalışır.  
  
##### <a name="to-access-unity-documentation"></a>Unity belgelerine erişmek için  
  
- Visual Studio 'da imleci vurgulayın veya hakkında bilgi edinmek istediğiniz Unity API 'sinin üzerine getirin, sonra **Ctrl + Alt + M, CTRL + H** tuşlarına basın  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior betik Sihirbazı  
 Unity 'de, çoğu komut dosyası MonoBehavior sınıfından türeterek ve yöntemlerinin bazılarını geçersiz kılarak uygulanır. Tek davranış Sihirbazı 'nı, aşırı yüklemek istediğiniz MonoBehavior yöntemlerinin boş tanımlarını hızlıca oluşturmak için kullanabilirsiniz. Bu Sihirbazı kullanarak, kullanılabilir yöntemler listesinden aşırı yüklemek istediğiniz bir veya daha fazla yöntem belirtebilir, kodunuza nereye ekleneceğine karar verebilir ve nasıl kullanıldıkları hakkında yorum dahil edilip edilmeyeceğini seçebilirsiniz.  
  
 ![MonoBehavior Sihirbazı iletişim kutusu.](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>MonoBehavior sihirbazını kullanarak boş MonoBehavior yöntemi tanımları oluşturmak için  
  
1. Visual Studio 'da, işaretçiyi yöntemlerin eklenmesini istediğiniz yere konumlandırın, sonra MonoBehavior sihirbazını başlatmak için **CTRL + SHIFT + e** tuşlarına basın. Ya da, zaten uygulanmış olan bir yeni yöntemleri eklemek istiyorsanız, daha sonra belirtebilirsiniz; yalnızca **CTRL + SHIFT + e**tuşlarına basın.  
  
2. Aşırı yüklemek istediğiniz yöntemleri seçin. **Betik yöntemleri oluştur** penceresinde, **oluşturulacak yöntemleri seçin**altında, yeniden yüklemek istediğiniz her yöntemin adının yanındaki onay kutusunu işaretleyin.  
  
3. **Framework sürümü** açılan menüsünde görüntülenen Çerçeve sürümünün kullanmakta olduğunuz sürümle eşleştiğinden emin olun. Eşleşmiyorsa, açılan listenin değerini kullanmak istediğiniz sürüm olarak değiştirin.  
  
4. Yöntemlerin nereye ekleneceğini seçin. Varsayılan olarak, Yöntemler İmlecin konumuna eklenir; bunları başka bir yere eklemek istiyorsanız, sınıfınızda zaten uygulanmış herhangi bir yöntemden sonra bunları eklemeyi seçebilirsiniz. Bu konumlardan birini seçmek için, **ekleme noktasının** değerini istediğiniz konuma değiştirin.  
  
5. Sihirbazın seçtiğiniz yöntemlere yorum oluşturmasını istiyorsanız, **Yöntem açıklamaları oluştur** onay kutusunu işaretleyin. Bu yorumlar, yöntemin ne zaman çağrıldığını ve genel sorumlulukların ne zaman olduğunu anlamanıza yardımcı olmak için tasarlanmıştır.  
  
6. Sihirbazdan çıkmak için **Tamam** düğmesini seçin ve yöntemleri kodunuza ekleyin.  
  
   Tek davranış Sihirbazı, özellikle Unity API 'sini öğrenirken veya alışık olduğunuz bir yöntemi aşırı yüklemeniz gerektiğinde faydalıdır. Unity API 'SI ile daha fazla karşılaştıkça, daha önce bildiğiniz yöntemleri hızlı bir şekilde oluşturmak için Hızlı MonoBehavior Sihirbazı 'nı tercih edebilirsiniz.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Hızlı MonoBehavior betik oluşturma Sihirbazı  
 Unity API 'sini zaten öğrenseniz, Hızlı MonoBehavior Sihirbazı 'Nı kullanarak aşırı yüklenmiş yöntemleri daha hızlı uygulayabilirsiniz. Bu Sihirbazı kullanarak, imleç konumunda yöntem açıklamaları olmadan eklenen yalnızca bir yöntem belirtebilirsiniz.  
  
 ![Hızlı MonoBehavior Sihirbazı iletişim kutusu.](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Hızlı MonoBehavior Sihirbazı 'nı kullanarak boş bir MonoBehavior yöntemi tanımı oluşturmak için  
  
1. Visual Studio 'da, işaretçiyi yöntemin eklenmesini istediğiniz yere konumlandırın, sonra Hızlı MonoBehavior sihirbazını başlatmak için **CTRL + SHIFT + Q** tuşlarına basın. Diğer MonoBehavior sihirbazından farklı olarak, yeni yöntem her zaman buraya eklendiği için, bu Sihirbazı kullanırken imleci kasıtlı olarak konumlandırmalısınız.  
  
2. **Betik yöntemi oluştur** penceresinin sağ üst köşesinde görüntülenen Çerçeve sürümünün kullanmakta olduğunuz sürümle eşleştiğinden emin olun. Eşleşmiyorsa, açılan listenin değerini kullanmak istediğiniz sürüm olarak değiştirin.  
  
3. Aşırı yüklemek istediğiniz yöntemi bulun. Betik yöntemi Oluştur penceresinde, metin kutusuna yöntemin adını yazmaya başlayın. Adları, girdiklerinizin bulunduğu yöntemlerin bir listesi görüntülenir.  
  
4. Aşırı yüklemek istediğiniz yöntemi seçin. İstediğiniz yöntem listede görüntülendiğinde fare veya ok tuşlarıyla seçin, sonra **ENTER**tuşuna basın. Listedeki tek yöntem ise yalnızca **ENTER**tuşuna basabilirsiniz. Yöntemi kodunuza eklenir.  
  
### <a name="unity-project-explorer"></a>Unity Proje Gezgini  
 Unity Proje Gezgini ' ni Visual Studio içinde Unity projenizde gezinmek için kullanabilirsiniz.  
  
 ![Unity Proje Gezgini penceresi.](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Unity proje Gezginini görüntülemek için  
  
- Visual Studio 'da, ana menüden **Görünüm**, **Unity Proje Gezgini**' ni seçin. Klavye: **alt + SHIFT + E**  
  
   ![Unity Proje Gezgini penceresini görüntüleyin.](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Unity Proje Gezgini tüm Unity proje dosyalarınızı ve dizinlerinizi Unity düzenleyiciyle aynı şekilde gösterir; bu, yalnızca betik dosyalarınızı içeren Çözüm Gezgini Unity betiklerinizde gezinmeden farklıdır ve bunları Unity için Visual Studio Araçları düzenleyen projeler ve çözümler olarak görüntüler. Özellikle büyük projelerde, Unity proje gezginini kullanarak değiştirmek istediğiniz betiği bulmak genellikle daha kolay olur; Ayrıca, Visual Studio 'da diğer dosya türlerini (örneğin, metin tabanlı yapılandırma dosyaları) Visual Studio çözümündeki projelerden birine eklemeden değiştirmek de kolaylaşır.  
  
### <a name="unity-error-list"></a>Unity Hata Listesi  
 Bir Unity örneğine bağlı olduğunda, Visual Studio 'nun içindeki Unity konsolundan bulunan iletileri görüntüleyebilirsiniz. Bu, Unity 'den hata ve uyarı içerir. İletiler, Visual Studio 'nun **hata listesi** penceresinde görüntülenir; Unity 'den hata iletileri **hatalar** sekmesinde görüntülenir, **Uyarılar** sekmesinde uyarı iletileri ve diğer Iletiler (örneğin, Debug. log Unity API kullanılarak gönderilen iletiler) **iletiler** sekmesinde görüntülenir.  
  
 İletileri görmek için Unity projenizin, betik hata ayıklamasını desteklemek ve Visual Studio sürümünüz için doğru olan Unity için Visual Studio Araçları paketini içe aktarmak için [bir Unity yürütücüsünde projenizde hata ayıklamalıdır](#debugging-your-project-in-a-unity-player) ve Visual Studio 'Nun [Visual Studio 'Yu Unity 'ye bağlanması](#connecting-visual-studio-to-unity)gerekir.  
  
 Visual Studio 'nun **hata listesi** penceresinde Unity 'den hataları, uyarıları ve iletileri görmek istemiyorsanız, bunları yapılandırma menüsünde devre dışı bırakabilirsiniz.  
  
### <a name="keyboard-shortcuts"></a>Klavye kısayolları  
 Visual Studio işlevselliği için Unity araçlarına, klavye kısayollarını kullanarak hızlıca erişebilirsiniz. Mevcut kısayolların özeti aşağıda verilmiştir.  
  
|Komut|Kısayol|Kısayol komutu adı|  
|-------------|--------------|---------------------------|  
|MonoBehavior sihirbazını açın|**Ctrl+Shift+M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|  
|Hızlı MonoBehavior sihirbazını açın|**Ctrl+Shift+Q**|**EditorContextMenus. CodeWindow. QuickMonoBehaviours**|  
|Unity proje Gezginini açın|**Alt + SHIFT + E**|**View. Unityprojecbir**|  
|Unity belgelerine erişin|**Ctrl + Alt + M, CTRL + H**|**Help. UnityAPIReference**|  
|Unity hata ayıklayıcıya (oynatıcı veya düzenleyici) iliştirme|**_Varsayılan değer yok_**|**Debug. AttachUnityDebugger**|  
  
 Varsayılan ' i beğenmezseniz kısayol tuşu kombinasyonlarını değiştirebilirsiniz. Nasıl değiştirileceği hakkında bilgi için bkz. [Visual Studio 'Da klavye kısayollarını tanımlama ve özelleştirme](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Unity hata ayıklaması  
 Unity için Visual Studio Araçları, Visual Studio 'nun güçlü hata ayıklayıcısını kullanarak Unity projeniz için hem Düzenleyici hem de oyun betiklerinin hatalarını ayıklamanızı sağlar.  
  
### <a name="connecting-visual-studio-to-unity"></a><a name="connecting-visual-studio-to-unity"></a> Visual Studio 'Yu Unity 'ye bağlama  
 Unity için Visual Studio Araçları, bir UDP bağlantısıyla Unity ile iletişim kurar. Bu, yerel olarak veya ağınız üzerinde herhangi bir yerde çalışan bir Unity örneğine tam olarak aynı şekilde bağlanabildiğiniz anlamına gelir. **Unity örneği Seç** iletişim kutusunu kullanarak ağınızda görebileceğiniz Unity örneklerinden birine bağlanabilirsiniz.  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Unity örneğini Seç iletişim kutusunu açmak için  
  
- Visual Studio 'da, ana menüden **Hata Ayıkla**, **Unity hata ayıklayıcı Ekle**öğesini seçin.  
  
     ![Unity hata ayıklayıcısını iliştirin.](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
- *Ya*da Visual Studio 'da durum çubuğunda, Visual Studio 'nun sağ alt köşesindeki tak simgesini seçin.  
  
     ![Bu simge, VSTU 'nin Unity 'ye bağlı olduğunu gösterir.](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
> Tak simgesi bir onay işareti gösteriyorsa, zaten bir Unity örneğine bağlanırsınız.  
  
 **Unity örneği Seç** iletişim kutusu, bağlandığınız her Unity örneğiyle ilgili bazı bilgileri görüntüler.  
  
 ![Bağlanılacak Unity örneğini seçin.](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Project**  
 Unity 'nin bu örneğinde çalışan Unity projesinin adı.  
  
 **Makine**  
 Bu Unity örneğinin üzerinde çalıştığı bilgisayarın veya cihazın adı.  
  
 **Tür**  
 Unity 'nin bu örneği Unity Düzenleyicisi 'nin bir parçası olarak çalışıyorsa **Düzenleyici** ; Bu Unity örneği tek başına bir oynatıcı ise **oynatıcı** .  
  
 **Bağlantı noktası**  
 Bu Unity örneğinin iletişim kurduğu UDP yuvasının bağlantı noktası numarası.  
  
> [!IMPORTANT]
> Unity için Visual Studio Araçları ve Unity örneği bir UDP ağ yuvası üzerinden iletişim kurduğundan, güvenlik duvarınız hakkında sorun olabilir. Bu durumda, VSTU ve Unity 'nin iletişim kurabilmesi için bağlantıyı yetkilendirmeniz gerekir.  
  
### <a name="debugging-your-project-in-a-unity-player"></a><a name="debugging-your-project-in-a-unity-player"></a> Unity oynatıcıda projenizde hata ayıklama  
 Unity düzenleyicisini çalıştırmıyorsanız veya platforma özgü sorunları ayıkladığınızda, tek başına bir oyuncu üzerinde çalışan Unity uygulamanıza doğrudan Unity için Visual Studio Araçları bağlayabilirsiniz.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Unity Player 'da betik hata ayıklamasını etkinleştirmek için  
  
- Betik hata ayıklaması etkinken bir geliştirme derlemesi oluşturmadığınızdan emin olun. Unity projenizin derleme ayarlarında, **geliştirme derlemesi** ve **betik hata ayıklama** onay kutularını işaretleyin.  
  
  ![Hata ayıklama için Unity derleme ayarlarını yapılandırın.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  Ayrıca, **Unity Web Player**'da çalışan bir Unity uygulamasında hata ayıklamak Için, **geliştirme sürümü kanalını**kullanmak üzere yapılandırmanız da gerekir.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Unity Web Player 'da geliştirme sürümü kanalını yapılandırmak için  
  
- Unity Web yürütücüsünün bağlam menüsünde, **yayın kanalı** ' nı seçin ve **geliştirme** seçeneğinin etkinleştirildiğinden emin olun.  
  
  > [!IMPORTANT]
  > Unity 4,2 ve üzeri sürümlerde, **yayın kanalı** bağlam menüsü öğesi yalnızca, kısayol menüsü açıldığında **alt** tuşuna basıldığında Web oynatıcı bağlam menüsünde kullanılabilir. Web oynatıcı Mac OS X üzerinde çalışıyorsa, bunun yerine **seçenek** tuşuna basın.  
  
  Son olarak, hata ayıklamak istediğiniz Unity örneğine bağlı olduğunuzdan emin olun. Bunun nasıl yapılacağı hakkında bilgi için bkz. [Visual Studio 'Yu Unity 'ye bağlama](#connecting-visual-studio-to-unity) bölümü.  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Unity projenizde DLL hatalarını ayıklama  
 Birçok Unity geliştiricisi, geliştirme işlevlerinin diğer projelerle kolayca paylaşılması için kod bileşenlerini dış dll 'Ler olarak yazıyor. Unity için Visual Studio Araçları, bu DLL 'Lerdeki kodun, Unity projenizdeki diğer kodla sorunsuz bir şekilde ayıklanabilmesini kolaylaştırır.  
  
> [!NOTE]
> Şu anda Unity için Visual Studio Araçları yalnızca yönetilen DLL 'Leri destekler. C++ dilinde yazılmış olanlar gibi yerel kod dll 'Lerinde hata ayıklamayı desteklemez.  
  
 Burada açıklanan senaryo kaynak koda sahip olduğunuzu varsayar. Yani, kendi birinci taraf kodunuzu geliştirdiğinizi veya yeniden kullandığınızı veya bir üçüncü taraf kitaplığına kaynak kodu kullandığınızı ve bunu bir DLL olarak Unity projenizde dağıtmayı planladığınızı unutmayın. Bu senaryo, kaynak kodu olmayan bir DLL 'nin hata ayıklamasını tanımlamaz.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity projenizde kullanılan bir yönetilen DLL projesinde hata ayıklamak için  
  
1. Mevcut DLL projenizi Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio çözümüne ekleyin. Daha az yaygın olarak, Unity projenizde kod bileşenleri içeren yeni bir yönetilen DLL projesi başlatıyorsunuz olabilirsiniz; Bu durumda, bunun yerine Visual Studio çözümüne yeni bir yönetilen DLL projesi ekleyebilirsiniz. Bir çözüme yeni veya var olan bir proje ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir çözüme proje ekleme](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).  
  
    ![Varolan DLL projenizi çözüme ekleyin.](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    Her iki Unity için Visual Studio Araçları durumda da, proje başvurusunu ve çözüm dosyalarını yeniden oluşturmak zorunda olsa bile, bu adımları yalnızca bir kez gerçekleştirmeniz gerekir.  
  
2. DLL projesinde doğru Unity Framework profiline başvurun. Visual Studio 'da, DLL projesinin özelliklerinde, **hedef Framework** özelliğini kullandığınız Unity çerçevesi sürümü olarak ayarlayın. Bu, projenizin hedeflediği, Unity Full, mikro veya Web temel sınıf kitaplıkları gibi API uyumluluğuyla eşleşen Unity temel sınıf kitaplığıdır. Bu, DLL 'nizin diğer çerçeveler veya uyumluluk düzeylerinde bulunan ancak kullanmakta olduğunuz Unity çerçevesi sürümünde mevcut olmayan çerçeve yöntemlerini aramasını engeller.  
  
    ![DLL 'nin hedef çerçevesini Unity çerçevesi olarak ayarlayın.](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. DLL 'yi Unity projenizin varlık klasörüne kopyalayın. Unity 'de varlıklar, çalışma zamanında yüklenebilmeleri için paketlenmiş ve Unity uygulamanız ile birlikte dağıtılan dosyalardır. Dll 'Ler çalışma zamanında bağlı olduğundan, dll 'Ler varlık olarak dağıtılmalıdır. Bir varlık olarak dağıtılması için Unity Düzenleyicisi, dll 'Lerin Unity projenizdeki varlıklar klasörünün içine yerleştirilmesi gerekir. Bunu iki şekilde yapabilirsiniz:  
  
   - DLL projenizin derleme ayarlarını, çıkış DLL ve PDB dosyalarını, çıktı klasöründen Unity projenizin **varlıklar** klasörüne kopyalayan bir oluşturma sonrası görevi içerecek şekilde değiştirin.  
  
   - Çıkış klasörünü Unity projenizin **varlıklar** klasörü olacak şekilde ayarlamak için dll projenizin derleme ayarlarını değiştirin. Hem DLL hem de PDB dosyaları **varlıklar** klasörüne yerleştirilir.  
  
     DLL 'nin hata ayıklama sembollerini içerdiğinden ve DLL kodunu kaynak kodu formuyla eşlediklerinden, PDB dosyaları hata ayıklama için gereklidir. Unity için Visual Studio Araçları dll oluşturmak için DLL ve PDB 'deki bilgileri kullanacaktır. , Unity betik altyapısı tarafından kullanılan hata ayıklama sembol biçimi olan MDB dosyası.  
  
4. Kodunuzda hata ayıklayın. Artık DLL kaynak kodunuzda, Unity projenizin kaynak kodu ile birlikte hata ayıklama yapabilir ve kesme noktaları ve kod üzerinden atlama gibi tüm hata ayıklama özelliklerini kullanabilirsiniz.

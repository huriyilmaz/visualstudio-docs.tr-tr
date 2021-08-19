---
title: Bir uygulamanın el ClickOnce dağıtma
description: Komut satırı sürümünü veya ClickOnce sürümünü kullanarak bir dağıtım oluşturma hakkında bilgi Bildirim Oluşturma ve Düzenleme Aracı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 83bc3a73bede906f23dfc2b561bc3e2e3179af81
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153777"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>İzlenecek yol: ClickOnce uygulamasını el ile dağıtma
Uygulamanızı dağıtmak için Visual Studio veya Güvenilen Uygulama Dağıtımı gibi gelişmiş dağıtım özelliklerini kullanıyorsanız bildirimlerinizi oluşturmak içinMage.exekomut satırı aracını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanmalısınız. Bu kılavuzda, komut satırı sürümünü (Mage.exe) veya uygulamanın grafik sürümünü (MageUI.exe) kullanarak dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bildirim Oluşturma ve Düzenleme Aracı.****

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzda, dağıtımdan önce seçmeniz gereken bazı önkoşullar ve seçenekler vardır.

- yükleme *Mage.exe* ve *MageUI.exe.*

   *Mage.exe* ve *MageUI.exe,* 'nin bir [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] parçasıdır. yüklü veya ile [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] birlikte bulunan sürümünün yüklü olması [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Visual Studio. Daha fazla bilgi için [msdn'Windows SDK'sı](https://www.microsoft.com/download/details.aspx?id=8279) konusuna bakın.

- Dağıtıla bir uygulama sağlama.

   Bu kılavuzda, dağıtıma hazır Windows bir uygulamanın olduğu varsaylanır. Bu uygulama AppToDeploy olarak adlandırılır.

- Dağıtımın nasıl dağıtılacaklarını belirleme.

   Dağıtım seçenekleri şunlardır: Web, dosya paylaşımı veya CD. Daha fazla bilgi için [bkz. ClickOnce ve Dağıtım.](../deployment/clickonce-security-and-deployment.md)

- Uygulamanın yükseltilmiş bir güven düzeyi gerektirdiğini belirleme.

   Uygulamanıza Tam Güven (örneğin, kullanıcının sistemine tam erişim) gerektiriyorsa, bunu ayarlamak içinMage.exe`-TrustLevel` seçeneğini kullanabilirsiniz.  Uygulamanıza yönelik özel bir izin kümesi tanımlamak için İnternet veya intranet izni bölümünü başka bir bildirimden kopyalayıp, kendi ihtiyaçlarınıza uyacak şekilde değiştirebilir ve bir metin düzenleyicisi ya da bir metin düzenleyici kullanarak uygulama bildirimine *MageUI.exe.* Daha fazla bilgi için bkz. [Güvenilen Uygulama Dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

- Authenticode sertifikası alın.

   Dağıtımınızı bir Authenticode sertifikasıyla imzalamanız gerekir. Visual Studio, *MageUI.exe,* MakeCert.exevePvk2Pfx.exearaçlarını kullanarak bir  test sertifikası *oluşturabilirsiniz* veya bir Sertifika Yetkilisi'den (CA) bir sertifika edinebilirsiniz. Güvenilen Uygulama Dağıtımı kullanmayı seçerseniz, sertifikanın tüm istemci bilgisayarlara tek kullanımlık bir yüklemesini de gerçekleştirmeniz gerekir. Daha fazla bilgi için bkz. [Güvenilen Uygulama Dağıtımına Genel Bakış.](../deployment/trusted-application-deployment-overview.md)

  > [!NOTE]
  > Dağıtımınızı bir Sertifika Yetkilisini elde etmek için bir CNG sertifikasıyla da imza atabilirsiniz.

- Uygulamanın UAC bilgilerine sahip bir bildirime sahip olmadığını emin olun.

   Uygulamanıza öğe gibi Kullanıcı Hesabı Denetimi (UAC) bilgileri içeren bir bildirim olup olmadığını belirlemeniz `<dependentAssembly>` gerekir. Bir uygulama bildirimini incelemek için Sysinternals [Sigcheck](/sysinternals/downloads/sigcheck) Windows yardımcı programını kullanabilirsiniz.

   Uygulamanız UAC ayrıntılarını içeren bir bildirim içeriyorsa UAC bilgileri olmadan yeniden derlemeniz gerekir. Bir C# projesi için Visual Studio proje özelliklerini açın ve Uygulama sekmesini seçin. Bildirim **açılan listesinde** Bildirim olmadan uygulama **oluştur'a tıklayın.** Bir Visual Basic projesinde Visual Studio özelliklerini açın, Uygulama sekmesini seçin ve **UAC'yi** görüntüle'ye tıklayın Ayarlar. Açılan bildirim dosyasında, tek öğe içindeki tüm öğeleri `<asmv1:assembly>` kaldırın.

- Uygulamanın istemci bilgisayarda önkoşullar gerektirdiğini belirleme.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]bir önkoşul olan Visual Studio önkoşul yükleme önyükleyicisi (*setup.exe*) içerebilir. Bu izlenecek yol, bir dağıtım için gereken iki bildirimi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] oluşturur. GenerateBootstrapper görevini kullanarak önkoşul [önyükleyicisi oluşturabilirsiniz.](../msbuild/generatebootstrapper-task.md)

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Komut satırı aracını kullanarak Mage.exe dağıtmak için

1. Dağıtım dosyalarınızı depolayacak bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dizin oluşturun.

2. Yeni oluşturduğunuz dağıtım dizininde bir sürüm alt dizini oluşturun. Uygulamayı ilk kez dağıtıyorsanız sürüm alt dizinine **1.0.0.0 adını girin.**

   > [!NOTE]
   > Dağıtım sürümünüz, uygulamanın sürümünden farklı olabilir.

3. Tüm uygulama dosyalarınızı yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları da dahil olmak üzere sürüm alt dizinine kopyalayın. Gerekirse, ek dosyalar içeren ek alt dizinler oluşturabilirsiniz.

4. veya [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] komut Visual Studio açın ve sürüm alt dizinine yazın.

5. Mage.exeçağrısıyla *uygulama bildirimini oluşturun.* Aşağıdaki deyim, Intel x86 işlemcisinde çalıştıracak şekilde derlenmiş kod için bir uygulama bildirimi oluşturur.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Geçerli dizini gösteren seçeneğin sonrası olan noktayı (.) `-FromDirectory` dahil etmek istediğinizden emin olun. Nokta belirtmezseniz uygulama dosyalarınızın yolunu belirtmeniz gerekir.

6. Uygulama bildirimini Authenticode sertifikanız ile imzalar. *mycert.pfx dosyasını* sertifika dosyanıza giden yol ile değiştirin. *passwd'i* sertifika dosyanız için parolayla değiştirin.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Visual Studio ve Windows SDK ile dağıtılan .NET Framework 4.6.2 SDK'sı ile *mage.exe,* bildirimleri hem CNG hem de Authenticode sertifikaları ile imzalar. Authenticode sertifikalarla aynı komut satırı parametrelerini kullanın.

7. Dağıtım dizininin kök dizinine kadar olan bölümü seçin.

8. bir çağrısıyla dağıtım bildirimini *Mage.exe.* Varsayılan olarak *Mage.exe,* hem çevrimiçi hem de çevrimdışı çalıştırılamayacak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] şekilde dağıtımınızı yüklü bir uygulama olarak işaretlemektedir. Uygulamayı yalnızca kullanıcı çevrimiçi olduğunda kullanılabilir yapmak için değerini `-Install` kullanarak seçeneğini `false` kullanın. Varsayılanı kullanırsanız ve kullanıcılar web sitesinden veya dosya paylaşımından uygulamanızı yükleyecekse, seçeneğin değerinin Web sunucusunda veya paylaşımında uygulama bildiriminin konumunu `-ProviderUrl` göstermesini sağlar.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Authenticode veya CNG sertifikanız ile dağıtım bildirimini imzalar.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Dağıtım dizininde yer alan tüm dosyaları dağıtım hedefine veya medyaya kopyalayın. Bu bir Web sitesinde veya FTP sitesinde bulunan bir klasör, dosya paylaşımı veya CD-ROM olabilir.

11. Kullanıcılarınıza, uygulamalarınızı yüklemek için gereken URL' yi, UNC'yi veya fiziksel medyayı belirtin. Bir URL veya UNC sağlarsanız, kullanıcılarınıza dağıtım bildiriminin tam yolunu vermalısınız. Örneğin, AppToDeploy AppToDeploy dizininde 'ye http://webserver01/ dağıtılırsa, tam URL yolu http://webserver01/AppToDeploy/AppToDeploy.application olur.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Uygulamanın grafik aracıyla MageUI.exe için

1. Dağıtım dosyalarınızı depolayacak bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dizin oluşturun.

2. Yeni oluşturduğunuz dağıtım dizininde bir sürüm alt dizini oluşturun. Uygulamayı ilk kez dağıtıyorsanız sürüm alt dizinine **1.0.0.0 adını girin.**

   > [!NOTE]
   > Dağıtım sürümünüz büyük olasılıkla uygulamanın sürümünden farklıdır.

3. Tüm uygulama dosyalarınızı yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları da dahil olmak üzere sürüm alt dizinine kopyalayın. Gerekirse, ek dosyalar içeren ek alt dizinler oluşturabilirsiniz.

4. Grafik *MageUI.exe* aracını başlatma.

   ```cmd
   MageUI.exe
   ```

5. Menüden Dosya , Yeni , Uygulama **Bildirimi'yi seçerek** **yeni bir uygulama** bildirimi oluşturun. 

6. Varsayılan Ad **sekmesinde,** bu dağıtımın adını ve sürüm numarasını yazın. Ayrıca, **x86** gibi, uygulamanın yerleşik olduğu İşlemciyi belirtin.

7. Dosyalar **sekmesini** ve ardından Uygulama dizini metin kutusunun yanındaki üç nokta (**...**) **düğmesini** seçin. Klasöre **Gözat iletişim** kutusu görüntülenir.

8. Uygulama dosyalarınızı içeren sürüm alt dizinini ve ardından Tamam'ı **seçin.**

9. Internet Information Services 'den (IIS) dağıtacaksanız, **.deploy** uzantısını doldurmak için .deploy uzantısını sahip olmadığınız herhangi bir dosyaya ekle onay kutusunu seçin.

10. Tüm uygulama **dosyalarınızı dosya** listesine eklemek için Doldurmak düğmesine gidin. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, Dosya Türü açılan listesinden  Giriş Noktası'ı seçerek bu dağıtım için ana yürütülebilir dosyayı başlangıç uygulaması olarak işaret edin.  (Uygulamanız yalnızca bir yürütülebilir dosya *içeriyorsaMageUI.exe* sizin için işaretlemektedir.)

11. Gerekli **İzinler** sekmesini seçin ve uygulamanıza onaylamanız gereken güven düzeyini seçin. Varsayılan **değer, çoğu uygulama** için uygun olacak olan FullTrust'tır.

12. Menüden Dosya , **Farklı Kaydet'i** seçin.  Uygulama bildirimini imzalamanız istendiğinde bir İmzalama Seçenekleri iletişim kutusu görüntülenir.

13. Dosya sisteminize dosya olarak depolanan bir sertifikanız  varsa, Sertifika dosyasıyla imzala seçeneğini kullanın ve üç nokta (**...**) düğmesini kullanarak dosya sisteminden sertifikayı seçin. Ardından sertifika parolanızı yazın.

     -veya-

     Sertifikanız bilgisayarınızdan erişilebilen bir sertifika depolamada tutuluyorsa, Depolanan sertifikayla imzala seçeneğini belirleyin ve sağlanan listeden sertifikayı seçin. 

14. Uygulama **bildiriminizi** imzalamak için Tamam'ı seçin. Farklı **Kaydet iletişim** kutusu görüntülenir.

15. Farklı **Kaydet iletişim** kutusunda sürüm dizinini belirtin ve Kaydet'i **seçin.**

16. Dağıtım **bildiriminizi** **oluşturmak** **için menüden Dosya** , Yeni , Dağıtım Bildirimi'ne tıklayın.

17. Ad **sekmesinde,** bu dağıtım için bir ad ve sürüm numarası belirtin (bu örnekte **1.0.0.0).** Ayrıca, **x86** gibi, uygulamanın yerleşik olduğu İşlemciyi belirtin.

18. Açıklama sekmesini **seçin** ve Publisher **ve** Product değerlerini **belirtin.** (**Ürün,** uygulamanıza çevrimdışı kullanım için Windows Başlat menüsü bir istemci bilgisayara yüklenirken uygulamanıza verilen addır.)

19. Dağıtım **Seçenekleri sekmesini** seçin ve Başlangıç **Konumu** metin kutusunda, Web sunucusunda veya paylaşımında uygulama bildiriminin konumunu belirtin. Örneğin, *\\ \myServer\myShare\AppToDeploy.application*.

20. Önceki bir adımda *.deploy uzantısını* eklediysanız burada .deploy dosya adı **uzantısını kullan'ı da** seçin.

21. Güncelleştirme **Seçenekleri sekmesini** seçin ve bu uygulamanın ne sıklıkta güncelleştirilsini istediğinizi belirtin. Uygulamanız <xref:System.Deployment.Application.UpdateCheckInfo> güncelleştirmeleri kendisi için kullanıyorsa Bu uygulama **güncelleştirmeleri** denetlemeli onay kutusunun işaretini kaldırın.

22. Uygulama **Başvurusu sekmesini** seçin ve bildirim seç **düğmesine** gidin. Açık bir iletişim kutusu görüntülenir.

23. Daha önce oluşturduğunuz uygulama bildirimini ve ardından Aç'ı **seçin.**

24. Menüden Dosya , **Farklı Kaydet'i** seçin.  Dağıtım **bildirimini** imzalamanızı istediğiniz bir İmzalama Seçenekleri iletişim kutusu görüntülenir.

25. Dosya sisteminize dosya olarak depolanan bir sertifikanız  varsa, Sertifika dosyasıyla imzala seçeneğini kullanın ve üç nokta (**...**) düğmesini kullanarak dosya sisteminden sertifikayı seçin. Ardından sertifika parolanızı yazın.

     -veya-

     Sertifikanız bilgisayarınızdan erişilebilen bir sertifika depolamada tutuluyorsa, Depolanan sertifikayla imzala seçeneğini belirleyin ve sağlanan listeden sertifikayı seçin. 

26. Dağıtım **bildiriminizi imzalamak** için Tamam'a gidin. Farklı **Kaydet iletişim** kutusu görüntülenir.

27. Farklı **Kaydet iletişim kutusunda,** dağıtım kök dizinine bir dizin yukarı taşının ve Kaydet'i **seçin.**

28. Dağıtım dizininde yer alan tüm dosyaları dağıtım hedefine veya medyaya kopyalayın. Bu bir Web sitesinde veya FTP sitesinde bulunan bir klasör, dosya paylaşımı veya CD-ROM olabilir.

29. Kullanıcılarınıza, uygulamalarınızı yüklemek için gereken URL' yi, UNC'yi veya fiziksel medyayı belirtin. Url veya UNC sağlarsanız, kullanıcılarınıza dağıtım bildiriminin tam yolunu vermalısınız. Örneğin, AppToDeploy AppToDeploy dizininde 'ye http://webserver01/ dağıtılırsa, tam URL yolu http://webserver01/AppToDeploy/AppToDeploy.application olur.

## <a name="next-steps"></a>Sonraki adımlar
 Uygulamanın yeni bir sürümünü dağıtmanız gerekirken, yeni sürümden (örneğin, 1.0.0.1) sonra adlı yeni bir dizin oluşturun ve yeni uygulama dosyalarını yeni dizine kopyalayın. Ardından, yeni bir uygulama bildirimi oluşturmak ve imzalamak ve dağıtım bildirimini güncelleştirmek ve imzalamak için önceki adımları izlemeniz gerekir. Yalnızca daha yüksek sürümleri güncelleştirmesi ve en sol tamsayı en *önemli olduğuMage.exe* ve çağrılarında aynı yüksek sürümü `-New` `-Update` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] belirtmeye dikkat edin. MageUI.exekullandıysanız, uygulamayı açarak, Uygulama Başvurusu sekmesini seçerek,  Bildirim Seç düğmesine  gidip güncelleştirilmiş uygulama bildirimini seçerek dağıtım bildirimini güncelleştirebilirsiniz. **

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)

---
title: 'İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d02a12c9c412e4dbcc83efc96fd5d8171f0d61b6
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806820"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanızı dağıtmak için Visual Studio 'yu kullanamaz veya güvenilir uygulama dağıtımı gibi gelişmiş dağıtım özelliklerini kullanmanız gerekiyorsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimlerinizi oluşturmak için *Mage. exe* komut satırı aracını kullanmanız gerekir. Bu izlenecek yol, Bildirim Oluşturma ve Düzenleme Aracı komut satırı sürümü (*Mage. exe*) veya grafik sürümü (*MageUI. exe*) kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımı oluşturmayı açıklar.

## <a name="prerequisites"></a>Prerequisites
 Bu kılavuzda, bir dağıtım oluşturmadan önce belirlemeniz gereken bazı Önkoşullar ve seçenekler bulunur.

- *Mage. exe* ve *MageUI. exe*' yi yükler.

   *Mage. exe* ve *mageuı. exe* [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]parçasıdır. [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] yüklü olmalıdır ya da Visual Studio ile birlikte sunulan [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] sürümü gerekir. Daha fazla bilgi için bkz. MSDN 'de [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) .

- Dağıtılacak bir uygulama sağlayın.

   Bu kılavuzda, dağıtıma hazırsanız bir Windows uygulamanız olduğunu varsaymaktadır. Bu uygulama AppToDeploy olarak anılacaktır.

- Dağıtımın nasıl dağıtılacağını belirleme.

   Dağıtım seçenekleri şunlardır: Web, dosya paylaşma veya CD. Daha fazla bilgi için bkz. [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).

- Uygulamanın yükseltilmiş bir güven düzeyi gerektirip gerektirmediğini belirleme.

   Uygulamanız tam güven gerektiriyorsa — Örneğin, kullanıcının sistemine tam erişim — bunu yapmak için *Mage. exe* ' nin `-TrustLevel` seçeneğini kullanabilirsiniz. Uygulamanız için özel bir izin kümesi tanımlamak istiyorsanız, Internet veya intranet izin bölümünü başka bir bildirimden kopyalayabilir, gereksinimlerinize uyacak şekilde değiştirebilir ve bir metin Düzenleyicisi ya da *MageUI. exe*kullanarak uygulama bildirimine ekleyebilirsiniz. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

- Bir Authenticode sertifikası edinin.

   Dağıtımınızı bir Authenticode sertifikasıyla imzalamanız gerekir. Visual Studio, *MageUI. exe*veya *MakeCert. exe* ve *Pvk2pfx. exe* araçlarını kullanarak bir test sertifikası OLUŞTURABILIR veya bir sertifika yetkilisinden (CA) bir sertifika edinebilirsiniz. Güvenilen uygulama dağıtımını kullanmayı seçerseniz, sertifikanın tüm istemci bilgisayarlara tek seferlik bir yüklemesini de gerçekleştirmeniz gerekir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > Ayrıca, dağıtımınızı bir sertifika yetkilisinden alabileceğiniz CNG sertifikasıyla imzalayabilirsiniz.

- Uygulamanın UAC bilgilerine sahip bir bildirimi olmadığından emin olun.

   Uygulamanızın bir `<dependentAssembly>` öğesi gibi kullanıcı hesabı denetimi (UAC) bilgilerini içeren bir bildirim içerip içermediğini belirlemeniz gerekir. Uygulama bildirimini incelemek için, Windows Sysinternals [Sigdenetim](/sysinternals/downloads/sigcheck) yardımcı programını kullanabilirsiniz.

   Uygulamanız UAC ayrıntıları içeren bir bildirim içeriyorsa, bunu UAC bilgileri olmadan yeniden derlemeniz gerekir. Visual Studio C# 'daki bir proje için, proje özelliklerini açın ve uygulama sekmesini seçin. **Bildirim** açılan listesinde, **bildirim olmadan uygulama oluştur**' u seçin. Visual Studio 'daki bir Visual Basic projesi için, proje özelliklerini açın, uygulama sekmesini seçin ve **UAC ayarlarını görüntüle**' ye tıklayın. Açılan bildirim dosyasında, tek `<asmv1:assembly>` öğesi içindeki tüm öğeleri kaldırın.

- Uygulamanın istemci bilgisayarda önkoşulları gerektirip gerektirmediğini belirleme.

   Visual Studio 'dan dağıtılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar, dağıtımınız ile bir önkoşul yükleme Önyükleyicisi (*Setup. exe*) içerebilir. Bu izlenecek yol, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımı için gereken iki bildirimi oluşturur. [GenerateBootstrapper görevini](../msbuild/generatebootstrapper-task.md)kullanarak bir önkoşul önyükleyici oluşturabilirsiniz.

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Bir uygulamayı Mage. exe komut satırı aracı ile dağıtmak için

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım dosyalarınızı depolayabileceğiniz bir dizin oluşturun.

2. Yeni oluşturduğunuz dağıtım dizininde, bir sürüm alt dizini oluşturun. Uygulamayı ilk kez dağıtıyorsanız, sürüm alt dizinini **1.0.0.0**olarak adlandırın.

   > [!NOTE]
   > Dağıtımınızın sürümü uygulamanızın sürümünden farklı olabilir.

3. Yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı sürüm alt dizinine kopyalayın. Gerekirse, ek dosyalar içeren ek alt dizinler oluşturabilirsiniz.

4. [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] veya Visual Studio komut istemi ' ni açın ve sürüm alt dizinine değiştirin.

5. *Mage. exe*çağrısıyla uygulama bildirimini oluşturun. Aşağıdaki ifade, Intel x86 işlemcisi üzerinde çalışmak üzere derlenen kod için bir uygulama bildirimi oluşturur.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Geçerli dizini belirten `-FromDirectory` seçeneğinden sonra nokta (.) eklediğinizden emin olun. Noktayı eklemezseniz, uygulama dosyalarınızın yolunu belirtmeniz gerekir.

6. Uygulama bildirimini Authenticode sertifikanıza imzalayın. *Mycert. pfx* dosyasını sertifika dosyanızın yoluyla değiştirin. *Passwd* değerini sertifika dosyanızın parolasıyla değiştirin.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Visual Studio ile dağıtılan ve Windows SDK ile birlikte .NET Framework 4.6.2 SDK ile başlayarak, *Mage. exe* bildirimleri, ve Authenticode sertifikalarıyla birlikte işaretler. Authenticode sertifikalarıyla aynı komut satırı parametrelerini kullanın.

7. Dağıtım dizininin köküne geçin.

8. *Mage. exe*çağrısıyla dağıtım bildirimini oluşturun. Varsayılan olarak, *Mage. exe* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımınızı yüklü bir uygulama olarak işaretleyecek ve bu sayede hem çevrimiçi hem de çevrimdışı çalıştırılabilirler. Uygulamayı yalnızca kullanıcı çevrimiçi olduğunda kullanılabilir hale getirmek için, `false`bir değerle `-Install` seçeneğini kullanın. Varsayılan değeri kullanırsanız ve kullanıcılar uygulamanızı bir Web sitesinden veya dosya paylaşımından yükleyeceksiniz, `-ProviderUrl` seçeneğinin değerinin Web sunucusunda veya paylaşımda bulunan uygulama bildiriminin konumunu işaret ettiğini doğrulayın.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Dağıtım bildirimini Authenticode veya CNG sertifikanız ile imzalayın.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Dağıtım dizinindeki tüm dosyaları dağıtım hedefine veya medyaya kopyalayın. Bu, bir Web sitesindeki veya FTP sitesindeki bir klasör, bir dosya paylaşımında veya bir CD-ROM olabilir.

11. Uygulamanızı yüklemek için kullanıcılarınıza gereken URL, UNC veya fiziksel medyayı sağlayın. Bir URL veya UNC sağlarsanız, kullanıcılarınıza dağıtım bildiriminin tam yolunu vermeniz gerekir. Örneğin, AppToDeploy, AppToDeploy dizininde http://webserver01/ dağıtılırsa, tam URL yolu http://webserver01/AppToDeploy/AppToDeploy.application olur.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI. exe grafik aracıyla bir uygulama dağıtmak için

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım dosyalarınızı depolayabileceğiniz bir dizin oluşturun.

2. Yeni oluşturduğunuz dağıtım dizininde, bir sürüm alt dizini oluşturun. Uygulamayı ilk kez dağıtıyorsanız, sürüm alt dizinini **1.0.0.0**olarak adlandırın.

   > [!NOTE]
   > Dağıtımınızın sürümü büyük olasılıkla uygulamanızın sürümünden farklıdır.

3. Yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı sürüm alt dizinine kopyalayın. Gerekirse, ek dosyalar içeren ek alt dizinler oluşturabilirsiniz.

4. *MageUI. exe* grafik aracını başlatın.

   ```cmd
   MageUI.exe
   ```

5. Menüden **Dosya**, **Yeni**, **uygulama bildirimi** ' ni seçerek yeni bir uygulama bildirimi oluşturun.

6. Varsayılan **ad** sekmesinde, bu dağıtımın adını ve sürüm numarasını yazın. Ayrıca, uygulamanızın oluşturulduğu **işlemciyi** (x86 gibi) belirtin.

7. **Dosyalar** sekmesini seçin ve **uygulama dizini** metin kutusunun yanındaki üç nokta ( **...** ) düğmesine tıklayın. **Klasöre yönelik bir araştır** iletişim kutusu görüntülenir.

8. Uygulama dosyalarınızı içeren sürüm alt dizinini seçin ve ardından **Tamam**' a tıklayın.

9. Internet Information Services (IIS) ' den **dağıtabuyorsanız, doldurma sırasında. deploy uzantısını bir dosyaya ekle** onay kutusunu seçin.

10. Tüm uygulama dosyalarınızı dosya listesine eklemek için **doldur** düğmesine tıklayın. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, **dosya türü** açılır listesinden **giriş noktası** ' nı seçerek bu dağıtım için ana yürütülebilir dosyayı başlangıç uygulaması olarak işaretleyin. (Uygulamanız yalnızca bir yürütülebilir dosya içeriyorsa, *MageUI. exe* bunu sizin için işaretleyecek.)

11. **Gerekli izinler** sekmesini seçin ve uygulamanız için gereken güven düzeyini seçin. Varsayılan değer **FullTrust**' dır. Bu, çoğu uygulama için uygun olacaktır.

12. Menüden **Dosya**, **farklı kaydet** ' i seçin. Uygulama bildirimini imzalamak isteyip istemediğinizi soran bir Imzalama seçenekleri iletişim kutusu görüntülenir.

13. Dosya sisteminizde bir dosya olarak depolanan bir sertifikanız varsa, **sertifika dosyası Ile imzala** seçeneğini kullanın ve üç nokta ( **...** ) düğmesini kullanarak dosya sisteminden sertifikayı seçin. Ardından sertifika parolanızı yazın.

     veya

     Sertifikanız bilgisayarınızdan erişilebilen bir sertifika deposunda tutuluyorsa, **depolanan sertifikayla imzala** seçeneğini belirleyin ve belirtilen listeden sertifikayı seçin.

14. Uygulama bildiriminizi imzalamak için **Tamam** ' ı tıklatın. **Farklı kaydet** iletişim kutusu görüntülenir.

15. **Farklı kaydet** iletişim kutusunda, sürüm dizinini belirtin ve ardından **Kaydet**' e tıklayın.

16. Dağıtım bildiriminizi oluşturmak için menüden **Dosya**, **Yeni**, **dağıtım bildirimi** ' ni seçin.

17. **Ad** sekmesinde, bu dağıtım için bir ad ve sürüm numarası belirtin (Bu örnekte**1.0.0.0** ). Ayrıca, uygulamanızın oluşturulduğu **işlemciyi** (x86 gibi) belirtin.

18. **Açıklama** sekmesini seçin ve **Yayımcı** ve **ürün**için değerleri belirtin. (**Ürün** , uygulamanız çevrimdışı kullanım için bir istemci bilgisayara yüklediğinde Windows Başlat menüsündeki uygulamanıza verilen addır.)

19. **Dağıtım seçenekleri** sekmesini seçin ve **Başlangıç konumu** metin kutusunda Web sunucusunda veya paylaşımda uygulama bildiriminin konumunu belirtin. Örneğin, *\Myserver\myshare\apptodeploy.exe\\* .

20. *. Deploy* uzantısını önceki bir adımda eklediyseniz de kullan ' ı seçin **. dosya adı uzantısını burada dağıtın** .

21. **Güncelleştirme seçenekleri** sekmesini seçin ve bu uygulamanın ne sıklıkta güncelleştirilmesini istediğinizi belirtin. Uygulamanız güncelleştirmelerin kendisini denetlemek için <xref:System.Deployment.Application.UpdateCheckInfo> kullanıyorsa, **Bu uygulamanın güncelleştirmeleri denetlemesi gerekir** onay kutusunun işaretini kaldırın.

22. **Uygulama başvurusu** sekmesini seçin ve ardından **bildirim Seç** düğmesine tıklayın. Aç iletişim kutusu görüntülenir.

23. Daha önce oluşturduğunuz uygulama bildirimini seçip **Aç**' a tıklayın.

24. Menüden **Dosya**, **farklı kaydet** ' i seçin. Dağıtım bildirimini imzalamanızı isteyen bir **Imzalama seçenekleri** iletişim kutusu görüntülenir.

25. Dosya sisteminizde bir dosya olarak depolanan bir sertifikanız varsa, **sertifika dosyası Ile imzala** seçeneğini kullanın ve üç nokta ( **...** ) düğmesini kullanarak dosya sisteminden sertifikayı seçin. Ardından sertifika parolanızı yazın.

     veya

     Sertifikanız bilgisayarınızdan erişilebilen bir sertifika deposunda tutuluyorsa, **depolanan sertifikayla imzala** seçeneğini belirleyin ve belirtilen listeden sertifikayı seçin.

26. Dağıtım bildiriminizi imzalamak için **Tamam** ' ı tıklatın. **Farklı kaydet** iletişim kutusu görüntülenir.

27. **Farklı kaydet** iletişim kutusunda, dağıtımınızın köküne bir dizin yukarı taşıyın ve **Kaydet**' e tıklayın.

28. Dağıtım dizinindeki tüm dosyaları dağıtım hedefine veya medyaya kopyalayın. Bu, bir Web sitesindeki veya FTP sitesindeki bir klasör, bir dosya paylaşımında veya bir CD-ROM olabilir.

29. Uygulamanızı yüklemek için kullanıcılarınıza gereken URL, UNC veya fiziksel medyayı sağlayın. Bir URL veya UNC sağlarsanız, kullanıcılarınıza dağıtım bildiriminin tam yolunu vermeniz gerekir. Örneğin, AppToDeploy, AppToDeploy dizininde http://webserver01/ dağıtılırsa, tam URL yolu http://webserver01/AppToDeploy/AppToDeploy.application olur.

## <a name="next-steps"></a>Sonraki adımlar
 Uygulamanın yeni bir sürümünü dağıtmanız gerektiğinde yeni sürümden sonra adlı yeni bir dizin oluşturun — örneğin, 1.0.0.1 — ve yeni uygulama dosyalarını yeni dizine kopyalayın. Ardından, yeni bir uygulama bildirimi oluşturup imzalamak ve dağıtım bildirimini güncelleştirmek ve imzalamak için önceki adımları izlemeniz gerekir. Yalnızca en önemli en büyük tamsayı ile, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yalnızca daha yüksek sürümleri güncelleştirdiği için *Mage. exe* `-New` ve `-Update` çağrılarında aynı yüksek sürümü belirttiğinizden dikkatli olun. *MageUI. exe*' yi kullandıysanız, dağıtım bildirimini açarak, **uygulama başvurusu** sekmesini seçerek, **bildirim Seç** düğmesine tıklayarak ve ardından güncelleştirilmiş uygulama bildirimini seçerek güncelleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
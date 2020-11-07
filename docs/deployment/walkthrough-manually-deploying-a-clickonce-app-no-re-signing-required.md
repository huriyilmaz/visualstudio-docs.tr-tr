---
title: Marka tutmayı & ClickOnce uygulamasını el ile dağıtın
description: Yeni bir dağıtım bildirimi oluşturmadan ve müşteri markasını kullanabilmeniz için müşteriler tarafından dağıtılacak ClickOnce uygulamaları oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29bdd080e87e8fad44c7b8943d0d017749b8c30b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350315"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>İzlenecek yol: yeniden imzalama gerektirmeyen ve marka bilgilerini koruyan bir ClickOnce uygulamasını El Ile dağıtın
Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama oluşturup bu uygulamayı yayımlamak ve dağıtmak üzere bir müşteriye verdiğinizde, müşterinin genellikle dağıtım bildirimini güncelleştirmesi ve yeniden imzalaması gerekiyordu. Çoğu durumda hala tercih edilen yöntem olsa da, 3,5 .NET Framework, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Yeni bir dağıtım bildirimini yeniden oluşturmak zorunda kalmadan müşteriler tarafından dağıtılabilecek dağıtımlar oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz. [sınama ve üretim sunucuları için teslim etmeden ClickOnce uygulamaları dağıtma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama oluşturup bu uygulamayı yayımlamak ve dağıtmak üzere bir müşteriye verdiğinizde, uygulama müşterinin markasını kullanabilir veya markalamayı koruyabilir. Örneğin, uygulama tek bir özel uygulama ise markanızı korumak isteyebilirsiniz. Uygulama her müşteri için yüksek düzeyde özelleştirildiyse, müşterinin markasını kullanmak isteyebilirsiniz. .NET Framework 3,5, bir kuruluşa dağıtmak üzere bir uygulama verdiğinizde markanızı, Yayımcı bilgilerini ve güvenlik imzanızı korumanıza olanak sağlar. Daha fazla bilgi için bkz. [diğer kullanıcıların dağıtması Için ClickOnce uygulamaları oluşturma](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> Bu kılavuzda, komut satırı aracı *Mage.exe* veya grafik araç *MageUI.exe* kullanarak dağıtımları el ile oluşturabilirsiniz. El ile dağıtımlar hakkında daha fazla bilgi için bkz. [Izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolda bulunan adımları gerçekleştirmek için aşağıdakiler gerekir:

- Dağıtmaya hazırsanız Windows Forms bir uygulama. Bu uygulama *WindowsFormsApp1* olarak anılacaktır.

- Visual Studio veya Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Mage.exe kullanarak birden çok dağıtım ve marka desteğiyle ClickOnce uygulaması dağıtmak için

1. Bir Visual Studio komut istemi veya bir [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] komut istemi açın ve dosyalarınızı depoladığınız dizine geçin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Dağıtımınızın geçerli sürümünden sonra adlı bir dizin oluşturun. Uygulamayı ilk kez dağıtıyorsanız, büyük olasılıkla **1.0.0.0** ' ı seçmeniz gerekir.

   > [!NOTE]
   > Dağıtımınızın sürümü uygulama dosyalarınızın sürümünden farklı olabilir.

3. **Bin** adlı bir alt dizin oluşturun ve yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere buradaki tüm uygulama dosyalarınızı kopyalayın.

4. Mage.exe çağrısıyla uygulama bildirimini oluşturun.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Uygulama bildirimini dijital sertifikanıza imzalayın.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Dağıtım bildirimini bir *Mage.exe* çağrısıyla oluşturun. *Mage.exe* , varsayılan olarak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımınızı yüklü bir uygulama olarak işaretleyecek ve bu sayede hem çevrimiçi hem de çevrimdışı olarak çalıştırılabilir. Uygulamayı yalnızca kullanıcı çevrimiçi olduğunda kullanılabilir hale getirmek için, `-i` bir değeri olan bağımsız değişkenini kullanın `f` . Bu uygulama birden çok dağıtım özelliğinden yararlandığından, `-providerUrl` *Mage.exe* bağımsız değişkenini dışlayın. (Sürüm 3,5 ' den önceki .NET Framework sürümlerinde, `-providerUrl` çevrimdışı bir uygulama için hariç tutularak hata oluşur.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Dağıtım bildirimini imzalayın.

8. Uygulamayı ağda dağıtacağı tüm dosyaları müşteriye sağlayın.

9. Bu noktada, müşteri dağıtım bildirimini kendi kendine oluşturulmuş sertifikasıyla imzalayamalıdır. Örneğin, müşteri Adventure Works adlı bir şirkette çalışıyorsa, *MakeCert.exe* aracını kullanarak kendinden imzalı bir sertifika oluşturabilir. Sonra, *MakeCert.exe* tarafından oluşturulan dosyaları *Mage.exe* geçirilebilecek bir PFX dosyasına birleştirmek için *Pvk2pfx.exe* aracını kullanın.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Daha sonra müşteri, dağıtım bildirimini imzalamak için bu sertifikayı kullanır.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Müşteri, uygulamayı kullanıcılarına dağıtır.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>MageUI.exe kullanarak birden çok dağıtım ve marka desteğiyle ClickOnce uygulaması dağıtmak için

1. Bir Visual Studio komut istemi veya bir [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] komut istemi açın ve dosyalarınızı depoladığınız dizine gidin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. **Bin** adlı bir alt dizin oluşturun ve yürütülebilir dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere buradaki tüm uygulama dosyalarınızı kopyalayın.

3. Dağıtımınızın geçerli sürümünden sonra adlı bir alt dizin oluşturun. Uygulamayı ilk kez dağıtıyorsanız, büyük olasılıkla **1.0.0.0** ' ı seçmeniz gerekir.

   > [!NOTE]
   > Dağıtımınızın sürümü uygulama dosyalarınızın sürümünden farklı olabilir.

4. \\ **Bin** dizinini adım 2 ' de oluşturduğunuz dizine taşıyın.

5. Grafik aracı *MageUI.exe* başlatın.

   ```cmd
   MageUI.exe
   ```

6. Menüden **Dosya** , **Yeni** , **uygulama bildirimi** ' ni seçerek yeni bir uygulama bildirimi oluşturun.

7. Varsayılan **ad** sekmesinde, bu dağıtımın adını ve sürüm numarasını girin. Ayrıca, **Yayımcı** için, dağıtıldığında başlangıç menüsündeki uygulamanın kısayol bağlantısı için klasör adı olarak kullanılacak bir değer sağlayın.

8. **Uygulama seçenekleri** sekmesini seçin ve **güven bilgileri Için uygulama bildirimini kullan** ' a tıklayın. Bu, bu uygulama için üçüncü taraf markalamayı etkinleştirir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

9. **Dosyalar** sekmesini seçin ve **uygulama dizini** metin kutusunun yanındaki **Git düğmesine tıklayın** .

10. 2. adımda oluşturduğunuz uygulama dosyalarınızı içeren dizini seçin ve klasör seçimi iletişim kutusunda **Tamam** ' a tıklayın.

11. Tüm uygulama dosyalarınızı dosya listesine eklemek için **doldur** düğmesine tıklayın. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, **dosya türü** açılır listesinden **giriş noktası** ' nı seçerek bu dağıtım için ana yürütülebilir dosyayı başlangıç uygulaması olarak işaretleyin. (Uygulamanız yalnızca bir yürütülebilir dosya içeriyorsa *MageUI.exe* bunu sizin için işaretleyecek.)

12. **Gerekli izinler** sekmesini seçin ve uygulamanız için gereken güven düzeyini seçin. Varsayılan değer, çoğu uygulama için uygun olacak şekilde **tam güvendir**.

13. **Dosya** ' yı seçin, menüden **kaydedin** ve uygulama bildirimini kaydedin. Uygulamayı kaydettiğinizde uygulama bildirimini imzalamanız istenir.

14. Dosya sisteminizde dosya olarak depolanan bir sertifikanız varsa, **sertifika dosyası olarak imzala** seçeneğini kullanın ve dosya sistemindeki sertifikayı, üç nokta ( **...** ) düğmesini kullanarak seçin.

     -veya-

     Sertifikanız, bilgisayarınızdan erişilebilen bir sertifika deposunda tutuluyorsa, **depolanan sertifikayla imzala seçeneğini** belirleyin ve belirtilen listeden sertifikayı seçin.

15. Dağıtım bildiriminizi oluşturmak için menüden **Dosya** , **Yeni** , **dağıtım bildirimi** ' ni seçin ve ardından **ad** sekmesine bir ad ve sürüm numarası sağlayın (Bu örnekte **1.0.0.0** ).

16. **Güncelleştirme** sekmesine geçin ve bu uygulamanın ne sıklıkta güncelleştirilmesini istediğinizi belirtin. Uygulamanız [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güncelleştirmeleri denetlemek için DAĞıTıM API 'sini kullanıyorsa, **Bu uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun işaretini kaldırın.

17. **Uygulama başvurusu** sekmesine geçin. **Bildirim Seç** düğmesine tıklayıp önceki adımlarda oluşturduğunuz uygulama bildirimini seçerek bu sekmedeki tüm değerleri önceden doldurabilirsiniz.

18. **Kaydet** ' i ve dağıtım bildirimini diske kaydet ' i seçin. Uygulamayı kaydettiğinizde uygulama bildirimini imzalamanız istenir. Bildirimi imzalamadan kaydetmek için **iptal** ' e tıklayın.

19. Tüm uygulama dosyalarını müşteriye sağlayın.

20. Bu noktada, müşteri dağıtım bildirimini kendi kendine oluşturulmuş sertifikasıyla imzalayamalıdır. Örneğin, müşteri Adventure Works adlı bir şirkette çalışıyorsa, *MakeCert.exe* aracını kullanarak kendinden imzalı bir sertifika oluşturabilir. Sonra, *MakeCert.exe* tarafından oluşturulan dosyaları *MageUI.exe* geçirilebilecek bir PFX dosyasına birleştirmek için *Pvk2pfx.exe* aracını kullanın.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Sertifika üretilerek, istemci artık *MageUI.exe* ' de dağıtım bildirimini açıp ardından kaydederek dağıtım bildirimini imzalar. İmzalama iletişim kutusu göründüğünde, müşteri, **sertifika dosyası olarak imzala** seçeneğini belirler ve DISKTE kaydedildiği pfx dosyasını seçer.

22. Müşteri, uygulamayı kullanıcılarına dağıtır.

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik Istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)

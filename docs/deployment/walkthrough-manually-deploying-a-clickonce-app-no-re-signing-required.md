---
title: Markayı ClickOnce uygulama & el ile dağıtma
description: Yeni bir dağıtım ClickOnce oluşturmadan ve müşteri markasını kullanamadan müşteriler tarafından dağıtılacak yeni uygulamalar oluşturma hakkında bilgi öğrenin.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: edcba59250fad70c2b18b35a8a14a3b95c8db251
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073740"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Adım adım kılavuz: Yeniden ClickOnce gerektirmeyen ve marka bilgilerini koruyan bir uygulamanın el ile dağıtımı
Bir uygulama güncelleştirmeyi ve ardından müşteriye yayımlama ve dağıtmayı sağlarken, müşterinin geleneksel olarak dağıtım bildirimini güncelleştirmesi ve yeniden [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] imzalaması gerekmektedir. Çoğu durumda bu hala tercih edilen yöntemdir ancak .NET Framework 3.5, yeni bir dağıtım bildirimini yeniden oluşturmak zorunda kalmadan müşteriler tarafından dağıtılabilir dağıtımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] oluşturmanıza olanak sağlar. Daha fazla bilgi için [bkz. ClickOnce ve üretim sunucuları için yeniden atamadan uygulama dağıtma.](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)

 Bir uygulama oluşturmanız ve ardından müşteriye yayımlaması ve dağıtması için bir uygulama vererek müşterinin markasını kullanabilir veya markanızı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] koruyabilirsiniz. Örneğin, uygulama tek bir özel uygulama ise, markanızı korumak istiyor olabilir. Uygulama her müşteri için yüksek oranda özelleştirilmişse müşterinin markasını kullanmak istiyor olabilir. 3.NET Framework 3.5 sürümü, bir kuruluşa dağıtacak bir uygulama vererek markanızı, yayımcı bilginizi ve güvenlik imzanızı korumanıza olanak sağlar. Daha fazla bilgi için, [bkz. ClickOnce dağıtan uygulamalar oluşturma.](../deployment/creating-clickonce-applications-for-others-to-deploy.md)

> [!NOTE]
> Bu kılavuzda, komut satırı aracını veyaMage.exegrafik aracını *kullanarak* el ile *dağıtımlarMageUI.exe.* El ile dağıtımlar hakkında daha fazla bilgi için [bkz. Kılavuz: El ile bir ClickOnce dağıtma.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzda yer alan adımları gerçekleştirmek için aşağıdakiler gerekir:

- Dağıtmaya Windows bir Windows Forms uygulaması. Bu uygulama *WindowsFormsApp1 olarak adlandırılır.*

- Visual Studio SDK'Windows yükleyin.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Birden çok dağıtım ClickOnce marka desteğine sahip bir uygulama dağıtmak için Mage.exe

1. Bir Visual Studio istemi veya komut istemi açın ve dosyalarınızı [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] depolay olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] değiştirebilirsiniz.

2. Dağıtımınızı geçerli sürümüne göre adlı bir dizin oluşturun. Uygulamayı ilk kez dağıtıyorsanız, büyük olasılıkla **1.0.0.0 'ı seçersiniz.**

   > [!NOTE]
   > Dağıtım sürümünüz, uygulama dosyalarınızın sürümünden farklı olabilir.

3. bin adlı bir alt dizin **oluşturun ve yürütülebilir** dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı buraya kopyalayın.

4. Uygulama bildirimini uygulama bildirimini Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Uygulama bildirimini dijital sertifikanız ile imzalar.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. bir çağrısıyla dağıtım bildirimini *Mage.exe.* Varsayılan *olarak,Mage.exe* hem çevrimiçi hem de çevrimdışı çalıştırılamayacak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] şekilde dağıtımınızı yüklü bir uygulama olarak işaretlemektedir. Uygulamayı yalnızca kullanıcı çevrimiçi olduğunda kullanılabilir yapmak için bağımsız `-i` değişkenlerini değeriyle `f` kullanın. Bu uygulama birden çok dağıtım özelliğindan yararlanacak olduğu için bağımsız değişkenlerini `-providerUrl`Mage.exe. ** (Uygulamanın .NET Framework 3.5'den önceki sürümlerinde, çevrimdışı bir uygulamanın hariç `-providerUrl` tutularak hataya neden olur.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Dağıtım bildirimini imzalamayın.

8. Uygulamayı ağına dağıtacak olan müşteriye tüm dosyaları sağlama.

9. Bu noktada müşterinin dağıtım bildirimini kendi kendi oluşturulan sertifikasıyla imzalaması gerekir. Örneğin, müşteri Adventure Works adlı bir şirkette çalışıyorsa,MakeCert.exearacını *kullanarak otomatikMakeCert.exe* oluşturabilirsiniz. Ardından, *Pvk2pfx.exe* tarafından oluşturulan dosyalarıMakeCert.exebir  PFX dosyasında birleştirmek için *Mage.exe.*

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Müşteri bundan sonra dağıtım bildirimini imzalamak için bu sertifikayı kullanır.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Müşteri uygulamayı kullanıcılarına dağıtır.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Birden çok dağıtım ClickOnce marka desteğine sahip bir uygulama dağıtmak için MageUI.exe

1. Bir Visual Studio komut istemi veya komut istemi açın ve dosyalarınızı [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] depolay olarak dizine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gidin.

2. bin adlı bir alt dizin **oluşturun ve yürütülebilir** dosyalar, derlemeler, kaynaklar ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı buraya kopyalayın.

3. Dağıtımınızı geçerli sürümüne göre adlı bir alt dizin oluşturun. Uygulamayı ilk kez dağıtıyorsanız, büyük olasılıkla **1.0.0.0 'ı seçersiniz.**

   > [!NOTE]
   > Dağıtım sürümünüz, uygulama dosyalarınızın sürümünden farklı olabilir.

4. Bin \\ **dizinini** 2. adımda oluşturduğunuz dizine taşıma.

5. grafik aracını *MageUI.exe.*

   ```cmd
   MageUI.exe
   ```

6. Menüden Dosya , Yeni , Uygulama **Bildirimi'yi seçerek** **yeni bir uygulama** bildirimi oluşturun. 

7. Varsayılan Ad **sekmesinde,** bu dağıtımın adını ve sürüm numarasını girin. Ayrıca, dağıtıldığında **Publisher** kısayol bağlantısı için klasör adı olarak kullanılacak Başlat menüsü için bir değer girin.

8. Uygulama Seçenekleri **sekmesini seçin ve** Güven Bilgileri için Uygulama **Bildirimini Kullan'a tıklayın.** Bu, bu uygulama için üçüncü taraf markasını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] etkinleştirir.

9. Dosyalar sekmesini **seçin** ve Uygulama Dizini **metin** kutusunun yanındaki **Gözat düğmesine** tıklayın.

10. 2. adımda oluşturduğunuz uygulama dosyalarınızı içeren dizini seçin ve klasör seçimi **iletişim kutusunda** Tamam'a tıklayın.

11. Tüm **uygulama dosyalarınızı** dosya listesine eklemek için Doldurmak düğmesine tıklayın. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, Dosya Türü açılan listesinden  Giriş Noktası'ı seçerek bu dağıtım için ana yürütülebilir dosyayı başlangıç uygulaması olarak işaret edin.  (Uygulamanız yalnızca bir yürütülebilir dosya *içeriyorsaMageUI.exe* sizin için işaretlemektedir.)

12. Gerekli **İzinler sekmesini** seçin ve uygulamanıza onaylamanız gereken güven düzeyini seçin. Varsayılan, **çoğu uygulama için** uygun olan Tam Güven'tir.

13. **Menüden** Dosya **,** Kaydet'i seçin ve uygulama bildirimini kaydedin. Uygulama bildirimini kaydedecek şekilde imzalamanız istenir.

14. Dosya sisteminize dosya olarak depolanan bir sertifikanız  varsa, Sertifika dosyası olarak oturum aç seçeneğini kullanın ve üç nokta ( ... )**düğmesini** kullanarak dosya sisteminden sertifikayı seçin.

     -veya-

     Sertifikanız bilgisayarınızdan erişilebilen bir sertifika depolamada tutuluyorsa, Depolanan sertifikayla imzala seçeneğini belirleyin ve sağlanan listeden sertifikayı seçin.

15.  Dağıtım **bildiriminizi** **oluşturmak** **için** menüden Dosya , Yeni , Dağıtım Bildirimi'yi seçin ve ardından Ad sekmesinde bir ad ve sürüm numarası (bu örnekte **1.0.0.0)** girin.

16. Güncelleştir **sekmesine geçiş** yapın ve bu uygulamanın ne sıklıkta güncelleştirilsini istediğinizi belirtin. Uygulamanız güncelleştirmeleri [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kontrol etmek için Dağıtım API'sini kullanıyorsa, Bu uygulama güncelleştirmeleri denetlemeli onay kutusunu **temizleyin.**

17. Uygulama Başvurusu **sekmesine** geçiş yapın. Bildirim Seç düğmesine tıklar ve önceki adımlarda  oluşturduğunuz uygulama bildirimini seçerek bu sekmede yer alan tüm değerleri önceden tamamlayabilirsiniz.

18. **Kaydet'i** seçin ve dağıtım bildirimini diske kaydedin. Uygulama bildirimini kaydedecek şekilde imzalamanız istenir. Bildirimi **imzalamadan** kaydetmek için İptal'e tıklayın.

19. Tüm uygulama dosyalarını müşteriye sağlama.

20. Bu noktada müşterinin dağıtım bildirimini kendi kendi oluşturulan sertifikasıyla imzalaması gerekir. Örneğin, müşteri Adventure Works adlı bir şirkette çalışıyorsa,MakeCert.exearacını *kullanarak otomatikMakeCert.exe* oluşturabilirsiniz. Ardından, *Pvk2pfx.exe* tarafından oluşturulan dosyalarıMakeCert.exebir  PFX dosyasında birleştirmek için *MageUI.exe.*

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Sertifika oluşturulurken müşteri artık dağıtım bildiriminiMageUI.exe'de *açarak ve* kaydederek dağıtım bildirimini imzalar. İmzalama iletişim kutusu görüntülendiğinde müşteri  Sertifika dosyası olarak oturum aç seçeneğini ve diske kaydedmış olduğu PFX dosyasını seçer.

22. Müşteri uygulamayı kullanıcılarına dağıtır.

## <a name="see-also"></a>Ayrıca bkz.
- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Makecert](/windows/desktop/SecCrypto/makecert)

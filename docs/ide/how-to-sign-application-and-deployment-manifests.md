---
title: 'Nasıl yapilir: Başvuru ve dağıtım bildirimlerini imzalayın'
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf25301095ac5ff438514c37f61337e46342860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596170"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Nasıl yapilir: Başvuru ve dağıtım bildirimlerini imzalayın

ClickOnce dağıtımını kullanarak bir uygulama yayımlamak istiyorsanız, uygulama ve dağıtım bildirimlerinin ortak/özel anahtar çiftiyle imzalanması ve Authenticode teknolojisi kullanılarak imzalanması gerekir. Bildirimleri Windows sertifika mağazasından veya önemli bir dosyadan bir sertifika kullanarak imzalayabilirsiniz.

ClickOnce dağıtımı hakkında daha fazla bilgi için [ClickOnce güvenlik ve dağıtım'a](../deployment/clickonce-security-and-deployment.md)bakın.

ClickOnce bildirimlerini imzalamak *.exe*tabanlı uygulamalar için isteğe bağlıdır. Daha fazla bilgi için bu belgenin "İmzasız manifestolar oluştur" bölümüne bakın.

Anahtar dosyaları oluşturma hakkında bilgi için [bkz: Genel-özel anahtar çifti oluşturun.](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)

> [!NOTE]
> Visual *Studio, .pfx* uzantılı yalnızca Kişisel Bilgi Alışverişi (PFX) anahtar dosyalarını destekler. Ancak, proje özelliklerinin **İmza** sayfasında **Mağaza'dan Seç'i** tıklatarak geçerli kullanıcının Windows sertifika deposundan diğer sertifika türlerini seçebilirsiniz.

## <a name="sign-using-a-certificate"></a>Sertifika kullanarak imzalama

1. Proje özellikleri penceresine gidin **(Çözüm Gezgini'ndeki** proje düğümüne sağ tıklayın ve **Özellikler'i**seçin). **İmzalama** sekmesinde, **ClickOnce onay** kutusunu işaretle seçeneğini belirleyin.

2. **Mağaza'dan Seç** düğmesini tıklatın.

     **Sertifika Seç** iletişim kutusu görüntülenir ve Windows sertifika mağazasının içeriğini görüntüler.

    > [!TIP]
    > **Sertifika özelliklerini görüntülemek için burayı tıklattığınızda,** Sertifika **Ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu, sertifika ve ek seçenekler hakkında ayrıntılı bilgiler içerir. Ek yardım bilgilerini görüntülemek için **Sertifikalar'ı** tıklatın.

3. Bildirimleri imzalamak için kullanmak istediğiniz sertifikayı seçin.

4. Ayrıca, **Timestamp sunucusu URL** metin kutusunda bir zaman damgası sunucusunun adresini belirtebilirsiniz. Bu, bildirimin ne zaman imzalandığını belirten bir zaman damgası sağlayan bir sunucudur.

## <a name="sign-using-an-existing-key-file"></a>Varolan bir anahtar dosyasını kullanarak imzalama

1. **İmzalama** sayfasında, **ClickOnce onay** kutusunu göster seçeneğini belirleyin.

2. **Dosyadan Seç** düğmesini tıklatın.

     **Dosya seç** iletişim kutusu görüntülenir.

3. Dosya **seç** iletişim kutusunda, kullanmak istediğiniz anahtar dosyasının konumuna *(.pfx)* göz atın ve sonra **Aç'ı**tıklatın.

    > [!NOTE]
    > Bu seçenek yalnızca *.pfx* uzantılı dosyaları destekler. Başka bir biçimde bir anahtar dosyanız veya sertifikanız varsa, bu dosyayı Windows sertifika deposunda saklayın ve sertifikayı seçin önceki yordamda açıklanmıştır. Seçili sertifikanın amacı kod imzalamayı içermelidir.

     Dosya iletişim kutusunu **açmak için Parola Yı Gir** görüntülenir. *(.pfx* dosyası zaten Windows sertifika mağazanızda depolanmışsa veya parola korumalı değilse, parola girmeniz istenmez.)

4. Anahtar dosyasına erişmek için parolayı girin ve sonra **Enter'u**seçin.

> [!NOTE]
> *.pfx* dosyası sertifika zincirleme bilgilerini içeremez. Varsa, aşağıdaki alma hatası oluşur: **Şifre çözme için sertifika ve özel anahtar bulamıyorum.** Sertifika zincirleme bilgilerini kaldırmak için *Certmgr.msc'yi* kullanabilir ve *.pfx dosyasını dışa aktarırken **tüm sertifikaları ekleme** seçeneğini devre dışı [kullanabilirsiniz.](/previous-versions/aa730868(v=vs.80))

## <a name="sign-using-a-test-certificate"></a>Test sertifikası kullanarak imzalama

1. **İmzalama** sayfasında, **ClickOnce onay** kutusunu göster seçeneğini belirleyin.

2. Test için yeni bir sertifika oluşturmak için **Test Sertifikası Oluştur** düğmesini tıklatın.

3. Test **Sertifikası Oluştur** iletişim kutusuna, test sertifikanızı güvence altına almaya yardımcı olmak için bir parola girin.

## <a name="generate-unsigned-manifests"></a>İmzalanmamış bildirimler oluşturma

ClickOnce bildirimlerini imzalamak *.exe*tabanlı uygulamalar için isteğe bağlıdır. Aşağıdaki yordamlar, imzasız ClickOnce bildirimlerinin nasıl oluşturacağıgöster.

> [!IMPORTANT]
> İmzalanmamış bildirimler, uygulamanızın geliştirilmesini ve test ini basitleştirebilir. Ancak, imzasız manifestolar üretim ortamında önemli güvenlik riskleri doğurmaktadır. ClickOnce uygulamanız internetten veya diğer kötü amaçlı kod kaynaklarından tamamen izole edilmiş bir intranet içindeki bilgisayarlarda çalışıyorsa, yalnızca imzasız bildirimler kullanmayı düşünün.

Varsayılan olarak, bir veya daha fazla dosya oluşturulan karmanın dışında olmadığı sürece ClickOnce otomatik olarak imzalı bildirimler oluşturur. Başka bir deyişle, tüm dosyalar karmaya dahil sayılsa bile, **ClickOnce bildirimlerini onay** kutusunu işaretlediğinde bile, başvuru sonuçlarını imzalı manifestolarda yayımlama.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>İmzalanmamış bildirimler oluşturmak ve oluşturulan karmadaki tüm dosyaları eklemek için

1. Karmadaki tüm dosyaları içeren imzasız bildirimler oluşturmak için, önce uygulamayı imzalı bildirimlerle birlikte yayımlamanız gerekir. Bu nedenle, önce clickonce önceki yordamlardan birini izleyerek gösterir ve sonra uygulamayı yayımlayın imzalayın.

2. **İmzalama** sayfasında, ClickOnce onay kutusunu **gösterir Kaydet'i** temizleyin.

3. Uygulamanızın yalnızca bir sürümünün kullanılabilmesi için yayımlama sürümünü sıfırlayın. Varsayılan olarak, Visual Studio bir uygulamayı her yayımladığınızda yayımlama sürümünün düzeltme numarasını otomatik olarak arttır. Daha fazla bilgi için [bkz: ClickOnce yayımlama sürümünü ayarlayın.](../deployment/how-to-set-the-clickonce-publish-version.md)

4. Uygulamayı yayımlayın.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>İmzalanmamış bildirimler oluşturmak ve oluşturulan karmadan bir veya daha fazla dosyayı hariç tutmak için

1. **İmzalama** sayfasında, ClickOnce onay kutusunu **gösterir Kaydet'i** temizleyin.

2. Uygulama **Dosyaları** iletişim kutusunu açın ve oluşturulan karmadan hariç tutmak istediğiniz dosyalar için **Karma'yı** **Dışlamaya** ayarlayın.

    > [!NOTE]
    > Karma bir dosya hariç bildirimlerin otomatik imza devre dışı kalmak için ClickOnce yapılandırır, bu nedenle ilk önceki yordamda gösterildiği gibi imzalı bildirimleri ile yayımlamak gerekmez.

3. Uygulamayı yayımlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Güçlü adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
- [Nasıl yapilir: Genel-özel anahtar çifti oluşturma](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [İmza lama sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md)
- [ClickOnce güvenlik ve dağıtım](../deployment/clickonce-security-and-deployment.md)

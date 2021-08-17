---
title: 'Nasıl yapılanlar: Uygulama ve dağıtım bildirimlerini imzalama'
description: Uygulama ve dağıtım bildirimlerini yayımlamak ClickOnce gereksinimleri hakkında bilgi edinebilirsiniz. İmzalama, .exe uygulamalar için isteğe bağlıdır.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 561c378d36ede0c8c0130bdf633e3cd699c5dbbeffb62c633c3ae157d37cdf2f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372886"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Nasıl yapılanlar: Uygulama ve dağıtım bildirimlerini imzalama

Uygulama ve dağıtım ClickOnce yayımlamak için, uygulama ve dağıtım bildirimlerinin ortak/özel anahtar çifti ile imzalandır ve Authenticode teknolojisi kullanılarak imzalandırmalısınız. Bildirimleri, sertifika depolamadan veya anahtar dosyasından Windows kullanarak imzalarsiniz.

Dağıtım hakkında daha fazla ClickOnce için bkz. [ClickOnce ve dağıtımı.](../deployment/clickonce-security-and-deployment.md)

ClickOnce bildirimlerinin imzalanması,.exe *uygulamalar* için isteğe bağlıdır. Daha fazla bilgi için bu belgenin "Imzasız bildirim oluşturma" bölümüne bakın.

Anahtar dosyaları oluşturma hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Ortak-özel anahtar çifti oluşturma.](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)

> [!NOTE]
> Visual Studio *.pfx* uzantısına sahip Exchange (PFX) anahtar dosyalarını destekler. Ancak proje özelliklerinin İmzalama sayfasındaki Depodan Seç'e tıklayarak geçerli kullanıcının  Windows sertifika  depolamadan diğer sertifika türlerini de seçebilirsiniz.

## <a name="sign-using-a-certificate"></a>Sertifika kullanarak imzalama

1. Proje özellikleri penceresine gidin (projedeki proje düğümüne sağ **tıklayın Çözüm Gezgini'yi** **seçin).** İmzalama **sekmesinde,** **İlke bildirimlerini ClickOnce onay** kutusunu seçin.

2. Mağazadan **Seç düğmesine** tıklayın.

     Sertifika **Seç iletişim** kutusu görüntülenir ve sertifika deposuna Windows görüntüler.

    > [!TIP]
    > Sertifika özelliklerini görüntülemek **için buraya tıklayın'a** tıklarsanız, **Sertifika Ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifika hakkında ayrıntılı bilgiler ve ek seçenekler içerir. Ek **yardım bilgilerini görüntülemek** için Sertifikalar'a tıklayın.

3. Bildirimleri imzalamak için kullanmak istediğiniz sertifikayı seçin.

4. Ayrıca, Zaman damgası sunucusu URL'si metin kutusunda bir **zaman damgası sunucusunun adresini belirtebilirsiniz.** Bu, bildirimin ne zaman imzalanacak olduğunu belirten bir zaman damgası sağlayan bir sunucudur.

## <a name="sign-using-an-existing-key-file"></a>Mevcut bir anahtar dosyasını kullanarak imzalama

1. İmzalama **sayfasında,** **İlke bildirimlerini ClickOnce onay** kutusunu seçin.

2. Dosyadan **Seç düğmesine** tıklayın.

     Dosya **Seç** iletişim kutusu görüntülenir.

3. Dosya **Seç iletişim** kutusunda, kullanmak istediğiniz anahtar dosyasının konumunu (*.pfx*) bulun ve aç'a **tıklayın.**

    > [!NOTE]
    > Bu seçenek yalnızca *.pfx uzantısına sahip dosyaları* destekler. Başka bir biçimde bir anahtar dosyanız veya sertifikanız varsa, bunu sertifika Windows depoda depolar ve önceki yordamda açıklanan sertifikayı seçin. Seçilen sertifikanın amacı kod imzalamayı içermeli.

     Dosya **açmak için parola girin** iletişim kutusu görüntülenir. *(.pfx* dosyası zaten sertifika Windows depoda depolanmışsa veya parola korumalı değilse parola girmeniz istendiğinde.)

4. Anahtar dosyasına erişmek için parolayı girin ve Enter tuşuna **basın.**

> [!NOTE]
> *.pfx dosyası* sertifika zincirleme bilgilerini dahil etmek için kullanılamaz. Böyle bir durumda aşağıdaki içeri aktarma hatası oluşur: **Şifre çözme için sertifika ve özel anahtar bulunamaz.** Sertifika zincirleme bilgilerini kaldırmak için *Certmgr.msc* [](/previous-versions/aa730868(v=vs.80)) kullanabilir ve  *.pfx dosyasını dışarı aktarıyorsanız Tüm sertifikaları dahil edin seçeneğini devre dışı abilirsiniz.

## <a name="sign-using-a-test-certificate"></a>Test sertifikası kullanarak imzalama

1. İmzalama **sayfasında,** **İlke bildirimlerini ClickOnce onay** kutusunu seçin.

2. Test için yeni bir sertifika oluşturmak için Test Sertifikası **Oluştur düğmesine** tıklayın.

3. Test Sertifikası **Oluştur iletişim kutusunda,** test sertifikanızı güvenli hale etmeye yardımcı olmak için bir parola girin.

## <a name="generate-unsigned-manifests"></a>Imzasız bildirim oluşturma

ClickOnce bildirimlerinin imzalanması,.exe *uygulamalar* için isteğe bağlıdır. Aşağıdaki yordamlar, imzasız bildirim oluşturma ClickOnce gösterir.

> [!IMPORTANT]
> Imzasız bildirim, uygulama geliştirme ve test etme sürecini basitleştirebilir. Ancak imzasız bildirimlerin üretim ortamında önemli güvenlik riskleri vardır. Yalnızca internetten veya diğer kötü amaçlı kod kaynaklarından tamamen yalıtılmış bir intranet içindeki bilgisayarlarda çalışan ClickOnce imzasız bildirimleri kullanmayı göz önünde bulundurabilirsiniz.

Varsayılan olarak, ClickOnce veya daha fazla dosya özel olarak oluşturulan karmanın dışında tutulmayacaksa otomatik olarak imzalı bildirim oluşturulur. Başka bir deyişle, Tüm dosyalar karmaya dahil edilirse, Uygulamanın yayımlanması, Uygulama bildirimini imzala onay kutusunun ClickOnce bildirimleriyle sonuç verir. 

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Imzasız bildirim oluşturmak ve oluşturulan karmaya tüm dosyaları eklemek için

1. Karmaya tüm dosyaları içeren imzasız bildirim oluşturmak için, önce uygulamayı imzalı bildirimlerle birlikte yayımlamanız gerekir. Bu nedenle, önce ClickOnce yordamlardan birini takip eden uygulama bildirimlerini imzalayın ve ardından uygulamayı yayımlayın.

2. İmzalama **sayfasında,** İlke **bildirimlerini ClickOnce kutusunun işaretini** kaldırın.

3. Uygulamanın yalnızca bir sürümünün kullanılabilir olacak şekilde yayımlama sürümünü sıfırlayın. Varsayılan olarak, Visual Studio yayımlama sürümünün düzeltme numarasını otomatik olarak artırır. Daha fazla bilgi için [bkz. Nasıl ClickOnce ayarlama.](../deployment/how-to-set-the-clickonce-publish-version.md)

4. Uygulamayı yayımlayın.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Imzasız bildirim oluşturmak ve oluşturulan karmadan bir veya daha fazla dosya dışlamak için

1. İmzalama **sayfasında,** İlke **bildirimlerini ClickOnce kutusunun işaretini** kaldırın.

2. Uygulama Dosyaları **iletişim** kutusunu açın ve  oluşturulan **karmadan** dışlamak istediğiniz dosyalar için Karma'yı Dışla olarak ayarlayın.

    > [!NOTE]
    > Bir dosyanın karmadan dışlanması, ClickOnce otomatik imzalanmasını devre dışı bırakmak üzere dosya yapılandırmaları yapılandırır, bu nedenle önceki yordamda gösterildiği gibi ilk olarak imzalı bildirimlerle yayımlamanız gerek değildir.

3. Uygulamayı yayımlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlandırılmış derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)
- [Nasıl: Ortak-özel anahtar çifti oluşturma](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [İmzalama sayfası, Project Tasarımcısı](../ide/reference/signing-page-project-designer.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)

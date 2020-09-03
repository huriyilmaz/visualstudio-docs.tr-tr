---
title: 'Nasıl yapılır: uygulama ve dağıtım bildirimlerini Imzalama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7924201f4cf58e1066434707a8453b0fe1913bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670730"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Nasıl Yapılır: Uygulama ve Dağıtım Bildirimlerini İmzalama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce dağıtımını kullanarak bir uygulama yayımlamak istiyorsanız, uygulama ve dağıtım bildirimlerinin bir ortak/özel anahtar çifti ile imzalanması ve Authenticode teknolojisi kullanılarak imzalanmış olması gerekir. Windows sertifika deposundan veya anahtar dosyasından bir sertifika kullanarak bildirimleri imzalayabilirsiniz.

 ClickOnce dağıtımı hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

 ClickOnce bildirimlerinin imzalanması,. exe tabanlı uygulamalar için isteğe bağlıdır. Daha fazla bilgi için bu belgenin "Imzasız bildirimleri oluşturma" bölümüne bakın.

 Anahtar dosyaları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: genel-özel anahtar çifti oluşturma](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yalnızca. pfx uzantılı kişisel bilgi değişimi (PFX) anahtar dosyalarını destekler. Ancak, proje özelliklerinin **imzalama** sayfasında **depodan Seç** ' i tıklatarak geçerli kullanıcının Windows sertifika deposundan diğer sertifika türlerini seçebilirsiniz.

### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Uygulama ve dağıtım bildirimlerini bir sertifika kullanarak imzalamak için

1. Proje özellikleri penceresine gidin ( **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Özellikler**' i seçin veya **Hızlı Başlat** penceresine **Proje özellikleri** yazın veya **Çözüm Gezgini** penceresinin içinde alt + ENTER ' a basın. **İmzalama** sekmesinde **ClickOnce bildirimlerini imzala** onay kutusunu seçin.

2. **Mağazadan Seç** düğmesine tıklayın.

     **Sertifika seç** iletişim kutusu görünür ve Windows sertifika deposunun içeriğini görüntüler.

    > [!TIP]
    > **Sertifika özelliklerini görüntülemek için buraya tıklayın**' a tıklarsanız, **sertifika ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu sertifikayla ilgili ayrıntılı bilgileri içerir ve ek seçenekleri içerir. Ek Yardım bilgilerini görüntülemek için **Sertifikalar** ' a tıklayabilirsiniz.

3. Bildirimleri imzalamak için kullanmak istediğiniz sertifikayı seçin.

4. Ayrıca, zaman damgası sunucusu **URL 'si** metin kutusunda bir zaman damgası sunucusunun adresini de belirtebilirsiniz. Bu, bildirimin ne zaman imzalandığını belirten bir zaman damgası sağlayan bir sunucusudur.

### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Mevcut bir anahtar dosyasını kullanarak uygulama ve dağıtım bildirimlerini imzalamak için

1. **İmzalama** sayfasında **ClickOnce bildirimlerini imzala** onay kutusunu seçin.

2. **Dosyadan seç** düğmesine tıklayın.

     **Dosya Seç** iletişim kutusu görüntülenir.

3. **Dosya Seç iletişim** kutusunda, kullanmak istediğiniz anahtar dosyasının (. pfx) konumuna gidin ve ardından **Aç**' a tıklayın.

    > [!NOTE]
    > Bu seçenek yalnızca. pfx uzantılı dosyaları destekler. Başka bir biçimde anahtar dosyası veya sertifikanız varsa, bunu Windows sertifika depolama alanında depolayın ve önceki yordamda açıklanan sertifikayı seçin. Seçilen sertifikanın amacı, kod imzalama içermelidir.

     **Dosyayı açmak için parola girin** iletişim kutusu görüntülenir. (. Pfx dosyası zaten Windows sertifika deponuzda depolanıyorsa veya parola korumalı değilse, parola girmeniz istenmez.)

4. Anahtar dosyasına erişmek için parolayı girin ve ENTER 'a basın.

### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Uygulama ve dağıtım bildirimlerini bir test sertifikası kullanarak imzalamak için

1. **İmzalama** sayfasında **ClickOnce bildirimlerini imzala** onay kutusunu seçin.

2. Test için yeni bir sertifika oluşturmak için, **test sertifikası oluştur** düğmesine tıklayın.

3. **Test sertifikası oluştur** iletişim kutusunda, test sertifikanızın güvenliğini sağlamaya yardımcı olmak için bir parola girin.

## <a name="generating-unsigned-manifests"></a>Imzasız bildirimler oluşturma
 ClickOnce bildirimlerinin imzalanması,. exe tabanlı uygulamalar için isteğe bağlıdır. Aşağıdaki yordamlarda, imzasız ClickOnce bildirimlerinin nasıl oluşturulacağı gösterilmektedir.

> [!IMPORTANT]
> İmzasız bildirimler, uygulamanızın geliştirilmesini ve test edilmesini kolaylaştırabilir. Ancak, imzasız bildirimler bir üretim ortamında önemli ölçüde güvenlik riskleri sunar. Yalnızca ClickOnce uygulamanız Internet 'ten veya diğer kötü amaçlı kod kaynaklarından tamamen yalıtılmış bir intranet içindeki bilgisayarlarda çalışıyorsa imzasız bildirimleri kullanmayı düşünün.

 Varsayılan olarak, bir veya daha fazla dosya özel olarak oluşturulan karmadan dışlanmamışsa, ClickOnce otomatik olarak imzalı bildirimler oluşturur. Diğer bir deyişle, **ClickOnce bildirimlerini imzala** onay kutusu işaretli olsa bile tüm dosyalar karma 'e dahil edilirse uygulamanın sonuçları imzalı bildirimler halinde yayınlanmasına neden olur.

#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>İmzasız bildirimler oluşturmak ve oluşturulan Karmadaki tüm dosyaları dahil etmek için

1. Karma içindeki tüm dosyaları içeren imzasız bildirimler oluşturmak için, önce uygulamayı imzalı bildirimlerle birlikte yayımlamanız gerekir. Bu nedenle, önce önceki yordamlardan birini izleyerek ClickOnce bildirimlerini imzalayın ve ardından uygulamayı yayımlayın.

2. **İmzalama** sayfasında, **ClickOnce bildirimlerini imzala** onay kutusunu temizleyin.

3. Uygulamanızın yalnızca bir sürümü kullanılabilir olacak şekilde yayımlama sürümünü sıfırlayın. Varsayılan olarak, Visual Studio, uygulamayı her yayımladığınızda Yayımla sürümünün Düzeltme numarasını otomatik olarak arttırır. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce Publish sürümünü ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Uygulamayı yayımlayın.

#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>İmzasız bildirimler oluşturmak ve oluşturulan karmadan bir veya daha fazla dosyayı dışlamak için

1. **İmzalama** sayfasında, **ClickOnce bildirimlerini imzala** onay kutusunu temizleyin.

2. **Uygulama dosyaları** iletişim kutusunu açın ve oluşturulan karmadan dışlamak istediğiniz dosyalar Için **karmayı** **hariç tut** olarak ayarlayın.

    > [!NOTE]
    > Bir dosyanın karma sunucudan dışlanması, ClickOnce 'ı otomatik imzalamayı devre dışı bırakacak şekilde yapılandırır, bu nedenle ilk olarak önceki yordamda gösterildiği gibi imzalı bildirimlerle yayımlamanız gerekmez.

3. Uygulamayı yayımlayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Tanımlayıcı adlı derlemeler](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [nasıl yapılır: genel-özel anahtar çifti](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) [imzalama sayfası, proje Tasarımcısı](../ide/reference/signing-page-project-designer.md) [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md) oluşturma

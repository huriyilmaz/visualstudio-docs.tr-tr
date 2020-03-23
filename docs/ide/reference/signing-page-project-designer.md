---
title: İmzalama Sayfası, Proje Tasarımcısı
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 516e2aaf4a55ad6422200f9fef1cbbf2d435af7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597340"
---
# <a name="signing-page-project-designer"></a>İmzalama Sayfası, Proje Tasarımcısı

Uygulama ve dağıtım bildirimlerini imzalamak ve derlemeyi (güçlü ad imzalama) imzalamak için **Proje Tasarımcısı'nın** **İmzalama** sayfasını kullanın.

Her iki görev de **İmzalama** sayfasında gerçekleştirilse de, uygulama ve dağıtım bildirimlerinin imzalanmasının derlemenin imzalanmasından farklı bir işlem olduğuna dikkat edin.

Ayrıca, anahtar dosya bilgilerinin saklanması, bildirim imzalama ve derleme imzalama için farklıdır. Bildirim imzalama için önemli bilgiler bilgisayarınızın şifreleme depolama veritabanında ve geçerli kullanıcının Windows sertifika deposunda depolanır. Derleme imzalama için önemli bilgiler yalnızca bilgisayarınızın şifreleme depolama veritabanında depolanır.

**İmzalama** sayfasına erişmek için Çözüm **Gezgini'nde**bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler'i**tıklatın. Proje **Tasarımcısı** göründüğünde, **İmzala** sekmesini tıklatın.

## <a name="application-and-deployment-manifest-signing"></a>Uygulama ve Dağıtım Bildirimi İmzalama

**ClickOnce onay** kutusunu gösterir imzalayın

Uygulama ve dağıtım bildirimlerini ortak/özel anahtar çiftiyle imzalamak için bu onay kutusunu seçin. Bunun nasıl yapılacılaştırılaçılacılacağı hakkinda daha fazla bilgi için [bkz.](../../ide/how-to-sign-application-and-deployment-manifests.md)

**Mağaza düğmesinden seçin**

Geçerli kullanıcının kişisel sertifika deposundan varolan bir sertifika seçmenize olanak tanır. Uygulama ve dağıtım bildirimlerinizi imzalamak için bu sertifikalardan birini seçebilirsiniz.

**Mağazadan Seç'i** tıklattığınızda, kişisel sertifika mağazanızda geçerli olan (süresi dolmamış) ve özel anahtarları olan sertifikaları listeleyen **Sertifika Seç** iletişim kutusunu açar. Seçtiğiniz sertifikanın amacı kod imzalamayı içermelidir.

**Görünüm sertifikası özelliklerini**tıklattığınızda, Sertifika **Ayrıntıları** iletişim kutusu görüntülenir. Bu iletişim kutusu, sertifika hakkında ayrıntılı bilgiler içerir ve ek seçenekler içerir. Ek Yardım bilgilerini görüntülemek için **sertifikalar hakkında daha fazla bilgi edinin'i** tıklatabilirsiniz.

**Dosya düğmesinden seçin**

Varolan bir anahtar dosyasından sertifika seçmenize olanak tanır.

**Dosyadan Seç'i** tıklattığınızda, sertifika tuşu (.pfx) dosyasını seçmenize olanak tanıyan **Dosya Seç** iletişim kutusunu açar. Dosya parola korumalı olmalı ve kişisel sertifika mağazanızda bulunamaz.

Dosya iletişim kutusunu **açmak için Parola Yı Gir** kutusuna sertifika anahtarı (.pfx) dosyasını açmak için bir parola girin. Parola bilgileri kişisel anahtar kapsayıcı listenizde ve kişisel sertifika mağazanızda saklanır.

**Test Sertifikası oluşturma** düğmesi

Sınama için bir sertifika oluşturmanıza olanak tanır. Test sertifikası ClickOnce uygulama nızı ve dağıtım bildirimlerinizi imzalamak için kullanılır.

Test **Sertifikası Oluştur'u** tıklattığınızda, test sertifikası için güçlü ad anahtarı dosyası için parola yazabileceğiniz **Test Sertifikası Oluştur** iletişim kutusunu açar. Dosyanın adı *projeadı*_TemporaryKey.pfx. Parola yazmadan **Tamam'ı** tıklatırsanız,.pfx dosyası şifreşifrelenmez.

**Timestamp sunucu URL** kutusu

İmzanızı zaman layan bir sunucunun adresini belirtir. Bir sertifika verdiğinizde, bu dış site uygulamanın imzalandığı zamanı doğrular.

## <a name="assembly-signing"></a>Montaj İmzalama

**Montaj** onay kutusunu imzalama

Derlemeyi imzalamak ve güçlü bir şekilde adlandırılmış bir anahtar dosyası oluşturmak için bu onay kutusunu seçin. **Proje Tasarımcısı'nı**kullanarak derlemeyi imzalama hakkında daha fazla bilgi için [bkz.](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)

Bu seçenek, derlemeyi imzalamak için Windows Yazılım Geliştirme Kiti (SDK) tarafından sağlanan Al.exe aracını kullanır. Al.exe hakkında daha fazla bilgi için [bkz.](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)

**Güçlü bir ad anahtarı dosya** listesi seçin

Derlemeyi imzalamak için kullanılan yeni veya varolan güçlü adlandırılmış anahtar dosyasını belirtmenizi sağlar. Varolan bir anahtar dosyasını seçmek için ** \<Gözat...>'yi** seçin.

Derlemeyi imzalamak için yeni bir anahtar dosyası oluşturmak için ** \<Yeni...>'yi** seçin. Anahtar dosya adını belirtmek ve anahtar dosyasını parolayla korumak için kullanabileceğiniz **Güçlü Ad Anahtarı** Oluştur iletişim kutusu görüntülenir. Parola en az 6 karakter uzunluğunda olmalıdır. Bir parola belirtirseniz, Bir Kişisel Bilgi Alışverişi (.pfx) dosyası oluşturulur; parola belirtmezseniz, güçlü bir şekilde adlandırılmış bir anahtar (.snk) dosyası oluşturulur.

**Parolayı Değiştir** düğmesini değiştir

Derlemeyi imzalamak için kullanılan Kişisel Bilgi Alışverişi (.pfx) anahtar dosyasının parolasını değiştirir.

**Parolayı Değiştir'i** tıklattığınızda **Anahtar Parolasını Değiştir** iletişim kutusunu açar. Bu iletişim kutusunda, **Eski parola** anahtar dosyasının geçerli parolasIdir. **Yeni parola** en az 6 karakter uzunluğunda olmalıdır. Parola bilgileri geçerli kullanıcının Windows sertifika deposunda depolanır.

**Gecikme işareti yalnızca** onay kutusu

Gecikme imzalamayı etkinleştirmek için bu onay kutusunu seçin.

Gecikme imzalı bir projenin çalışmayacağını ve debugged olamayacağını unutmayın. Ancak, geliştirme sırasında doğrulamayı atlama `-Vr` seçeneğiyle [Sn.exe 'yi (Güçlü Ad Aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool) kullanabilirsiniz.

> [!NOTE]
> Bir derlemeyi imzaladığınızda, her zaman özel bir anahtara erişemeyebilirsiniz. Örneğin, bir kuruluşun, geliştiricilerin günlük olarak erişemeyecekleri, sıkı korunan bir anahtar çifti olabilir. Ortak anahtar kullanılabilir olabilir, ancak özel anahtara erişim birkaç kişiyle sınırlıdır. Böyle bir durumda, genel anahtarı sağlamak için *gecikmeli* veya *kısmi imzayı* kullanabilirsiniz, montaj devre dışı bırakılına kadar özel anahtarın eklenmesini erteleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Derleme ve Bildirim İmzalamayı Yönetme](../../ide/managing-assembly-and-manifest-signing.md)
- [Nasıl Yapılır: Uygulama ve Dağıtım Bildirimlerini İmzalama](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Nasıl yapılır: Bir Meclis 'i İmzalayın (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Nasıl yapılır: Bütünleştirilmiş Kodu Tanımlayıcı Adla İmzalama](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Tanımlayıcı Adlı Derlemeler](/dotnet/framework/app-domains/strong-named-assemblies)

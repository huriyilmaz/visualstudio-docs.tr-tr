---
title: Bir gizlilik istemiyle özel bir önyükleyici oluşturma
description: yeni dosya sürümlerine ve derleme sürümlerine sahip derlemeler kullanılabilir olduğunda otomatik olarak güncelleştirilecek ClickOnce uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 5f0c34a56b610ee65f2f9d8d4ac506224950c302
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133620"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>İzlenecek yol: Bir gizlilik istemiyle özel bir önyükleyici oluşturma
yeni dosya sürümlerine ve derleme sürümlerine sahip derlemeler kullanılabilir olduğunda otomatik olarak güncelleştirilecek ClickOnce uygulamaları yapılandırabilirsiniz. Müşterilerinizin Bu davranışa izin vermesini sağlamak için bir gizlilik istemi görüntüleyebilirsiniz. Ardından, uygulamaya otomatik olarak güncelleştirme izni verip vermeyeceğinizi seçebilirler. Uygulamanın otomatik olarak güncelleştirmesine izin verilmiyorsa, yüklemez.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Güncelleştirme Izni oluştur iletişim kutusu
 Bir gizlilik istemi göstermek için, okuyucunun uygulama için otomatik güncelleştirmelere izin vermesini isteyen bir uygulama oluşturun.

#### <a name="to-create-a-consent-dialog-box"></a>Onay iletişim kutusu oluşturmak için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

2. **yeni Project** iletişim kutusunda, **Windows**' a ve ardından **WindowsFormsApplication**' e tıklayın.

3. **Ad** Için **ConsentDialog** yazın ve ardından **Tamam**' a tıklayın.

4. Tasarımcıda forma tıklayın.

5. **Özellikler** penceresinde, **metin** özelliğini **güncelleştirme onayı iletişim kutusunu** olarak değiştirin.

6. **araç kutusunda** **tüm Windows Forms**' ı genişletin ve bir **etiket** denetimini forma sürükleyin.

7. Tasarımcıda etiket denetimine tıklayın.

8. **Özellikler** penceresinde, **Görünüm** altındaki **metin** özelliğini aşağıdaki gibi değiştirin:

    Yüklemek üzere olduğunuz uygulama, Web üzerinde en son güncelleştirmeleri denetler. "Kabul ediyorum" seçeneğine tıklayarak, uygulamayı internetten güncelleştirmeleri otomatik olarak denetleyip yükleyecek şekilde yetkilendirirsiniz.

9. **Araç kutusu**' nda, formun ortasına bir **CheckBox** denetimi sürükleyin.

10. **Özellikler** penceresinde, **kabul** ediyorum ' u Için, **Düzen** altındaki **metin** özelliğini değiştirin.

11. **Araç kutusunda**, bir **düğme** denetimini formun sol altına sürükleyin.

12. **Özellikler** penceresinde, **devam** etmek için **Düzen** altındaki **metin** özelliğini değiştirin.

13. **Özellikler** penceresinde, **Tasarım** altındaki **(ad)** özelliğini devam **edbutton** olarak değiştirin.

14. **Araç kutusunda**, formun sağ alt kısmına bir **düğme** denetimi sürükleyin.

15. **Özellikler** penceresinde, **Düzen** altındaki **metin** özelliğini **iptal**' e değiştirin.

16. **Özellikler** penceresinde, **(ad)** özelliğini **Design** ' ın altında **CancelButton**' a değiştirin.

17. Tasarımcı 'da, CheckedChanged olay işleyicisini oluşturmak için **kabul** ediyorum onay kutusuna çift tıklayın.

18. Form1 kod dosyasında, CheckedChanged olay işleyicisi için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet1":::

19. Varsayılan olarak **devam** düğmesini devre dışı bırakmak için sınıf oluşturucusunu güncelleştirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet6":::

20. Form1 kod dosyasında, son kullanıcının çevrimiçi güncelleştirmelere onaylı olup olmadığını izlemek üzere bir Boole değişkeni için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet3":::

21. Tasarımcıda, tıklama olay işleyicisini oluşturmak için **devam** düğmesine çift tıklayın.

22. Form1 kod dosyasında, **ilerle** düğmesine Click olay işleyicisine aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet2":::


23. Tasarımcıda, Click olay işleyicisini oluşturmak için **iptal** düğmesine çift tıklayın.

24. Form1 kod dosyasında, **Cancel** düğmesine Click olay işleyicisi için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet4":::

25. Son Kullanıcı çevrimiçi güncelleştirmeleri onaylamaz bir hata döndürecek şekilde uygulamayı güncelleştirin.

     yalnızca Visual Basic geliştiricileri için:

    1. **Çözüm Gezgini**, **ConsentDialog**' a tıklayın.

    2. **Project** menüsünde **modül ekle**' ye ve ardından **ekle**' ye tıklayın.

    3. *Module1. vb* kod dosyasında aşağıdaki kodu ekleyin.

       :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb" id="Snippet7":::

    4. **Project** menüsünde, **consentdialog özellikleri**' ne tıklayın ve ardından **uygulama** sekmesine tıklayın.

    5. **Uygulama çerçevesini etkinleştir** seçeneğinin işaretini kaldırın.

    6. **Başlangıç nesnesi** açılan menüsünde **Module1** öğesini seçin.

       > [!NOTE]
       > uygulama çerçevesini devre dışı bırakmak, Windows XP görsel stilleri, uygulama olayları, giriş ekranı, tek örnekli uygulama ve daha fazlası gibi özellikleri devre dışı bırakır. daha fazla bilgi için bkz. [uygulama sayfası, Project tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Yalnızca Visual C# geliştiricileri için:

       *Program. cs* kod dosyasını açın ve aşağıdaki kodu ekleyin.

       :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs" id="Snippet5":::

26. **Derle** menüsünde **BuildSolution**' a tıklayın.

## <a name="create-the-custom-bootstrapper-package"></a>Özel önyükleyici paketi oluşturma
 son kullanıcılara gizlilik istemi 'ni göstermek için, güncelleştirme onayı iletişim kutusu uygulaması için özel bir önyükleyici paketi oluşturabilir ve bunu tüm ClickOnce uygulamalarınıza bir önkoşul olarak ekleyebilirsiniz.

 Bu yordam, aşağıdaki belgeleri oluşturarak özel bir önyükleyici paketinin nasıl oluşturulacağını gösterir:

- Önyükleyici içeriğini tanımlayacak bir *product.xml* bildirim dosyası.

- Paketinizin dizeler ve yazılım lisans koşulları gibi yerelleştirmeye özgü yönlerini listelemek için bir *package.xml* bildirim dosyası.

- Yazılım lisans koşulları için bir belge.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>1. Adım: önyükleyici dizinini oluşturmak Için

1. *%programfiles%\microsoft sdk \ Windows \v7.0a\bootstrapper\packages* içinde **updateconsentdialog** adlı bir dizin oluşturun.

    > [!NOTE]
    > Bu klasörü oluşturmak için yönetici ayrıcalıklarına sahip olmanız gerekebilir.

2. *UpdateConsentDialog* dizininde, *en*-adlı bir alt dizin oluşturun.

    > [!NOTE]
    > Her yerel ayar için yeni bir dizin oluşturun. Örneğin, fr ve de yerel ayarları için alt dizinler ekleyebilirsiniz. Bu dizinler, gerekirse Fransızca ve Almanca dizeleri ve dil paketlerini içerir.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>2. Adım: product.xml bildirim dosyasını oluşturmak Için

1. *product.xml* adlı bir metin dosyası oluşturun.

2. *product.xml* dosyasında aşağıdaki XML kodunu ekleyin. Mevcut XML kodunun üzerine yazdığınızdan emin olun.

    ```xml
    <Product
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      ProductCode="Microsoft.Sample.EULA">
      <!-- Defines the list of files to be copied on build. -->
      <PackageFiles CopyAllPackageFiles="false">
        <PackageFile Name="ConsentDialog.exe"/>
      </PackageFiles>

      <!-- Defines how to run the Setup package.-->
      <Commands >
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>
          <ExitCodes>
            <ExitCode Value="0" Result="Success" />
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />
            <DefaultExitCode Result="Fail"
              FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
      </Commands>

    </Product>
    ```

3. Dosyayı UpdateConsentDialog önyükleyici dizinine kaydedin.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>3. Adım: package.xml bildirim dosyasını ve yazılım lisans koşullarını oluşturmak Için

1. *package.xml* adlı bir metin dosyası oluşturun.

2. *package.xml* dosyasında, yerel ayarı tanımlamak ve yazılım lisans koşulları 'nı eklemek IÇIN aşağıdaki XML kodunu ekleyin. Mevcut XML kodunun üzerine yazdığınızdan emin olun.

    ```xml
    <Package
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
      Name="DisplayName"
      Culture="Culture"
      LicenseAgreement="eula.rtf">
      <PackageFiles>
        <PackageFile Name="eula.rtf"/>
      </PackageFiles>

      <!-- Defines a localizable string table for error messages. -->
      <Strings>
        <String Name="DisplayName">Update Consent Dialog</String>
        <String Name="Culture">en</String>
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>
      </Strings>
    </Package>
    ```

3. Dosyayı UpdateConsentDialog önyükleyici dizininde en alt dizine kaydedin.

4. Yazılım lisans koşulları için *EULA. rtf* adlı bir belge oluşturun.

    > [!NOTE]
    > Yazılım lisans koşulları lisanslama, garantiler, borçlar ve yerel yasalar hakkında bilgiler içermelidir. Bu dosyalar yerel ayara özgü olmalıdır, bu nedenle dosyanın MBCS veya UNICODE karakterlerini destekleyen bir biçimde kaydedildiğinden emin olun. Yazılım lisans koşullarının içeriğiyle ilgili hukuk departmanınıza başvurun.

5. Belgeyi *UpdateConsentDialog* önyükleyici dizinindeki en alt dizine kaydedin.

6. Gerekirse, her yerel ayar için yazılım lisans koşulları için yeni bir *package.xml* bildirim dosyası ve yeni bir *EULA. rtf* belgesi oluşturun. Örneğin, fr ve de yerel ayarlar için alt dizinler oluşturduysanız, ayrı package.xml bildirim dosyaları ve yazılım lisans koşulları oluşturun ve bunları fr ve de alt dizinlere kaydedin.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Güncelleştirme Onayı uygulamasını bir önkoşul olarak ayarlama
 Visual Studio, güncelleştirme onayı uygulamasını bir önkoşul olarak ayarlayabilirsiniz.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Güncelleştirme Onayı uygulamasını bir önkoşul olarak ayarlamak için

1. **Çözüm Gezgini**, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. **Project** menüsünde, *ProjectName* **özellikler**' e tıklayın.

3. **Yayımla** sayfasına ve sonra **Önkoşullar**' a tıklayın.

4. **Onay onayını Güncelleştir**' i seçin.

    > [!NOTE]
    > önkoşullar iletişim kutusunda güncelleştirme onayı iletişim kutusunu görmek için Visual Studio kapatıp yeniden açmanız gerekebilir.

5. **Tamam**'a tıklayın.

## <a name="create-and-test-the-setup-program"></a>Kurulum programını oluşturma ve test etme
 Güncelleştirme Onayı uygulamasını bir önkoşul olarak ayarladıktan sonra, uygulamanız için yükleyiciyi ve önyükleyici oluşturabilirsiniz.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Kurulum programını kabul ediyorum ' a tıklamayan bir şekilde oluşturmak ve test etmek için

1. **Çözüm Gezgini**, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. **Project** menüsünde, *ProjectName* **özellikler**' e tıklayın.

3. **Yayımla** sayfasına tıklayın ve **Şimdi Yayımla**' ya tıklayın.

4. Yayımlama çıkışı otomatik olarak açılmadığından, yayımlama çıktısına gidin.

5. *Setup.exe* programını çalıştırın.

     Kurulum programı, güncelleştirme onayı Iletişim kutusu yazılım lisans sözleşmesini gösterir.

6. Yazılım lisans sözleşmelerini okuyun ve kabul et'e **tıklayın.**

     Güncelleştirme Onayı İletişim Kutusu uygulaması görüntülenir ve şu metni gösterir: Yüklemek istediğiniz uygulama, Web'de en son güncelleştirmeleri denetler. Kabul Ediyorum'a tıklayarak, uygulamayı güncelleştirmeleri İnternet'e otomatik olarak denetleme yetkisi verecek şekilde yetkilendirebilirsiniz.

7. Uygulamayı kapatın veya İptal'e tıklayın.

     Uygulama bir hata gösteriyor: ApplicationName için sistem bileşenleri yüklerken bir *hata oluştu.* Tüm sistem bileşenleri başarıyla yüklenene kadar kurulum devam eder.

8. Aşağıdaki hata iletisini göstermek için Ayrıntılar'a tıklayın: Bileşen Güncelleştirme Onayı İletişim Kutusu şu hata iletisiyle yüklenemedi: "Otomatik güncelleştirme sözleşmesi kabul edilemedi." Aşağıdaki bileşenler yüklenemedi: - Güncelleştirme Onayı İletişim Kutusu

9. **Kapat**’a tıklayın.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Kabul ediyorum'a tıklayarak Kurulum programını oluşturmak ve test etmek için

1. Uygulama **Çözüm Gezgini** içinde, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. Proje Adı **Project** ProjeAdı *Özellikleri'ne* **tıklayın.**

3. Yayımla **sayfasına ve** ardından Şimdi Yayımla'ya **tıklayın.**

4. Yayımlama çıkışı otomatik olarak açılmazsa yayımlama çıkışına gidin.

5. Setup.exe *çalıştırın.*

     Kurulum programı, Güncelleştirme Onayı İletişim Kutusu yazılım lisans sözleşmesini gösterir.

6. Yazılım lisans sözleşmelerini okuyun ve kabul et'e **tıklayın.**

     Güncelleştirme Onayı İletişim Kutusu uygulaması görüntülenir ve şu metni gösterir: Yüklemek istediğiniz uygulama, Web'de en son güncelleştirmeleri denetler. Kabul Ediyorum'a tıklayarak, uygulamayı güncelleştirmeleri İnternet'e otomatik olarak denetleme yetkisi verecek şekilde yetkilendirebilirsiniz.

7. Kabul **Ediyorum'a** ve ardından Devam'a **tıklayın.**

     Uygulama yüklenmeye başlar.

8. Uygulama Yükleme iletişim kutusu görüntülenirse Yükle'ye **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
- [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)
- [Nasıl: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md)
- [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)
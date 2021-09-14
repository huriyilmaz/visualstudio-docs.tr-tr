---
title: Bir gizlilik istemiyle özel bir önyükleyici oluşturma
description: Yeni dosya sürümlerine ve ClickOnce sürümlerine sahip derlemeler kullanılabilir olduğunda otomatik olarak güncelleştirilecek şekilde uygulama yapılandırmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725382"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>İzlenecek yol: Bir gizlilik istemiyle özel bir önyükleyici oluşturma
Yeni dosya sürümlerine ClickOnce derlemeler kullanılabilir olduğunda, uygulamaları otomatik olarak güncelleştirecek şekilde yapılandırabilirsiniz. Müşterilerimizin bu davranışı onay olduğundan emin olmak için onlara bir gizlilik istemi görüntüabilirsiniz. Ardından uygulamaya otomatik olarak güncelleştirme izni verip verilmeyeceklerini seçebilirler. Uygulamanın otomatik olarak güncelleştirilmesine izin verilmiyorsa yüklenmez.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Güncelleştirme Onayı Oluştur iletişim kutusu
 Bir gizlilik istemi görüntülemek için, okuyucudan uygulama için otomatik güncelleştirmeleri onaylarken onay isteyen bir uygulama oluşturun.

#### <a name="to-create-a-consent-dialog-box"></a>Onay iletişim kutusu oluşturmak için

1. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

2. Yeni **Project** iletişim kutusunda, Windows'a ve ardından **WindowsFormsApplication 'a tıklayın.** 

3. Ad için **ConsentDialog yazın ve** Tamam'a  **tıklayın.**

4. Tasarımcıda forma tıklayın.

5. Özellikler penceresinde **Text** özelliğini Güncelleştirme Onayı **İletişim** **Kutusu olarak değiştirin.**

6. Araç **Kutusunda, Tüm** **Formlar'Windows genişletin** ve bir Etiket **denetimi** sürükleyerek forma yazın.

7. Tasarımcıda etiket denetimine tıklayın.

8. Özellikler **penceresinde,** Görünüm altındaki **Text** özelliğini **aşağıdakiyle** değiştirin:

    Yüklemekte olduğunuz uygulama, Web'de en son güncelleştirmeleri denetler. "Kabul Ediyorum" seçeneğine tıklayarak, uygulamayı güncelleştirmeleri İnternet'den otomatik olarak denetlemesi ve yüklemesi için yetkilendirebilirsiniz.

9. Araç **Kutusunda,** onay **kutusu denetimlerini** formun ortasına sürükleyin.

10. Özellikler penceresinde **Düzen** altındaki **Text özelliğini** Kabul **Ediyorum** **olarak değiştirin.**

11. Araç **Kutusunda,** düğme **denetimlerini** formun sol alta sürükleyin.

12. Özellikler penceresinde **Düzen** altındaki **Text özelliğini** Devam **olarak** **değiştirin.**

13. Özellikler **penceresinde,** Tasarım altındaki **(Ad) özelliğini** **ProceedButton olarak değiştirin.** 

14. Araç **Kutusunda,** düğme **denetimlerini** formun sağ alta sürükleyin.

15. Özellikler penceresinde **Düzen** altındaki **Text özelliğini Cancel** **olarak** **değiştirin.**

16. Özellikler **penceresinde,** Tasarım altındaki **(Ad) özelliğini** **CancelButton olarak değiştirin.** 

17. CheckedChanged olay işleyicisini **oluşturmak için** tasarımcıda Kabul Ediyorum onay kutusuna çift tıklayın.

18. Form1 kod dosyasında CheckedChanged olay işleyicisi için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet1":::

19. Devam düğmesini varsayılan olarak devre dışı bırakmak için **sınıf oluşturucusu** güncelleştirildi.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet6":::

20. Form1 kod dosyasında, son kullanıcının çevrimiçi güncelleştirmelere onay verdip onay vermezse izlemek için bir Boole değişkeni için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet3":::

21. Tasarımcıda Devam'a çift **tıklayarak** Tıklama olayı işleyicisini üretin.

22. Form1 kod dosyasında, Devam düğmesinin Click olay işleyicisi'ne aşağıdaki **kodu** ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet2":::


23. Click olayı işleyicisini oluşturmak **için tasarımcıda** İptal düğmesine çift tıklayın.

24. Form1 kod dosyasında, İptal düğmesi için Click olay işleyicisi için aşağıdaki **kodu** ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb" id="Snippet4":::

25. Son kullanıcı çevrimiçi güncelleştirmelere onay vermezse, uygulamayı hata döndürürken güncelleştirin.

     Yalnızca Visual Basic geliştiriciler için:

    1. Bu **Çözüm Gezgini** **ConsentDialog'a tıklayın.**

    2. Yeni **Project** Modül Ekle'ye **ve** ardından Ekle'ye **tıklayın.**

    3. *Module1.vb kod* dosyasına aşağıdaki kodu ekleyin.

       :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb" id="Snippet7":::

    4. Uygulama **Project** **ConsentDialog Özellikleri'ne ve** ardından Uygulama **sekmesine** tıklayın.

    5. Uygulama çerçevesini **etkinleştir'in işaretini kaldırın.**

    6. Başlangıç **nesnesi açılan** menüsünde **Modül1'i seçin.**

       > [!NOTE]
       > Uygulama çerçevesinin devre dışı bırakılması XP görsel stilleri, Windows, giriş ekranı, tek örnekli uygulama ve daha fazlası gibi özellikleri devre dışı bırakmanızı sağlar. Daha fazla bilgi için [bkz. Uygulama Sayfası, Project Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Yalnızca Visual C# geliştiricileri için:

       *Program.cs kod* dosyasını açın ve aşağıdaki kodu ekleyin.

       :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs" id="Snippet5":::

26. Derleme menüsünde **BuildSolution** 'a **tıklayın.**

## <a name="create-the-custom-bootstrapper-package"></a>Özel önyükleyici paketini oluşturma
 Gizlilik istemini son kullanıcılara göstermek için, Güncelleştirme Onayı İletişim Kutusu uygulaması için özel bir önyükleyici paketi oluşturabilir ve bunu tüm uygulamalarınızı önkoşul olarak ClickOnce.

 Bu yordamda, aşağıdaki belgeleri oluşturarak özel bir önyükleyici paketinin nasıl oluşturulacakları açıklanıyor:

- *Önyükleyicinin* product.xmlaçıklayan bir bildirim dosyası.

- Bir *package.xml* dizeler ve yazılım lisans koşulları gibi paketinizin yerelleştirmeye özgü yönlerini listeleye bir bildirim dosyasıdır.

- Yazılım lisans koşulları için bir belge.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>1. Adım: Önyükleyici dizinini oluşturmak için

1. *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* dizininde **UpdateConsentDialog** adlı bir dizin oluşturun.

    > [!NOTE]
    > Bu klasörü oluşturmak için yönetici ayrıcalıklarına ihtiyacınız olabilir.

2. *UpdateConsentDialog dizininde* en adlı bir alt dizin *oluşturun.*

    > [!NOTE]
    > Her yerel seçim için yeni bir dizin oluşturun. Örneğin, fr ve de yerelleri için alt dizinler ekleme. Bu dizinler, gerekirse Fransızca ve Almanca dizeleri ve dil paketlerini içerir.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>2. Adım: Bildirim product.xml oluşturmak için

1. product.xmladlı bir *metin dosyası oluşturun.*

2. product.xml *dosyasında* aşağıdaki XML kodunu ekleyin. Mevcut XML kodunun üzerine yazmayabilirsiniz.

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

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>3. Adım: package.xml bildirimi dosyasını ve yazılım lisans koşullarını oluşturmak için

1. package.xmladlı bir *metin dosyası oluşturun.*

2. Yerel *package.xml* tanımlamak ve yazılım lisans koşullarını dahil etmek için aşağıdaki XML kodunu ekleyin. Mevcut XML kodunun üzerine yazmayabilirsiniz.

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

3. Dosyayı UpdateConsentDialog önyükleyici dizininde en alt dizinine kaydedin.

4. Yazılım lisans koşulları için *eula.rtf* adlı bir belge oluşturun.

    > [!NOTE]
    > Yazılım lisans koşulları lisanslama, garantiler, borçlar ve yerel yasalar hakkında bilgi içerir. Bu dosyalar yerele özgü olmalıdır, bu nedenle dosyanın MBCS veya UNICODE karakterlerini destekleyen bir biçimde kaydedildiklerine emin olun. Yazılım lisans koşullarının içeriği hakkında hukuk departmanınıza danışın.

5. *UpdateConsentDialog* önyükleyici dizininde belgeyi en alt dizinine kaydedin.

6. Gerekirse, her yerel *package.xml* lisans koşulları için yeni bir bildirim dosyası ve *yeni bir eula.rtf* belgesi oluşturun. Örneğin, fr ve de yerelleri için alt dizinler oluşturduysanız, ayrı package.xml bildirim dosyaları ve yazılım lisans koşulları oluşturun ve bunları fr ve de alt dizinlerine kaydedin.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Güncelleştirme Onayı Uygulamasını önkoşul olarak ayarlama
 Bu Visual Studio, Güncelleştirme Onayı uygulamasını önkoşul olarak ayarlayın.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Güncelleştirme Onayı Uygulamasını önkoşul olarak ayarlamak için

1. Uygulama **Çözüm Gezgini** içinde, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. Proje Adı **Project** ProjeAdı *Özellikleri'ne* **tıklayın.**

3. Yayımla **sayfasına ve** ardından Önkoşullar'a **tıklayın.**

4. Onay İletişim **Kutusunu Güncelleştir'i seçin.**

    > [!NOTE]
    > Önkoşullar İletişim Kutusunda Visual Studio İletişim Kutusunu görmek için bu iletişim kutusunu kapatıp yeniden açabilirsiniz.

5. **Tamam**'a tıklayın.

## <a name="create-and-test-the-setup-program"></a>Kurulum programını oluşturma ve test edin
 Güncelleştirme Onayı uygulamasını önkoşul olarak ayardikten sonra, uygulamanız için yükleyiciyi ve önyükleyiciyi oluşturabilirsiniz.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Kabul ediyorum'a tıklamadan Kurulum programını oluşturmak ve test etmek için

1. Uygulama **Çözüm Gezgini** içinde, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. Proje Adı **Project** ProjeAdı *Özellikleri'ne* **tıklayın.**

3. Yayımla **sayfasına ve** ardından Şimdi Yayımla'ya **tıklayın.**

4. Yayımlama çıkışı otomatik olarak açılmazsa yayımlama çıkışına gidin.

5. Setup.exe *çalıştırın.*

     Kurulum programı, Güncelleştirme Onayı İletişim Kutusu yazılım lisans sözleşmesini gösterir.

6. Yazılım lisans sözleşmesini okuyun ve ardından **kabul et**' e tıklayın.

     Güncelleştirme Onayı Iletişim kutusu uygulaması görünür ve şu metni gösterir: yüklemek üzere olduğunuz uygulama, Web üzerinde en son güncelleştirmeleri denetler. Kabul ediyorum ' a tıklayarak, uygulamayı Internet 'te güncelleştirmeleri otomatik olarak denetleyecek şekilde yetkilendirirsiniz.

7. Uygulamayı kapatın veya Iptal ' e tıklayın.

     Uygulama bir hata gösterir: *ApplicationName* için sistem bileşenleri yüklenirken bir hata oluştu. Tüm sistem bileşenleri başarıyla yüklenene kadar kurulum devam edemez.

8. Ayrıntılar ' a tıklayarak şu hata iletisini görüntüleyin: bileşen güncelleştirme onayı Iletişim kutusu şu hata iletisiyle başarısız oldu: "otomatik güncelleştirme sözleşmesi kabul edilmedi." Şu bileşenler yüklenemedi:-onay onay Iletişim kutusu

9. **Kapat**’a tıklayın.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Kurulum programını kabul ediyorum ' a tıklayarak oluşturma ve test etme

1. **Çözüm Gezgini**, dağıtmak istediğiniz uygulamanızın adına tıklayın.

2. **Project** menüsünde, *ProjectName* **özellikler**' e tıklayın.

3. **Yayımla** sayfasına tıklayın ve **Şimdi Yayımla**' ya tıklayın.

4. Yayımlama çıkışı otomatik olarak açılmadığından, yayımlama çıktısına gidin.

5. *Setup.exe* programını çalıştırın.

     Kurulum programı, güncelleştirme onayı Iletişim kutusu yazılım lisans sözleşmesini gösterir.

6. Yazılım lisans sözleşmesini okuyun ve ardından **kabul et**' e tıklayın.

     Güncelleştirme Onayı Iletişim kutusu uygulaması görünür ve şu metni gösterir: yüklemek üzere olduğunuz uygulama, Web üzerinde en son güncelleştirmeleri denetler. Kabul ediyorum ' a tıklayarak, uygulamayı Internet 'te güncelleştirmeleri otomatik olarak denetleyecek şekilde yetkilendirirsiniz.

7. **Kabul** ediyorum ' a ve ardından **devam**' a tıklayın.

     Uygulama yüklenmeye başlıyor.

8. Uygulama yüklemesi iletişim kutusu görüntülenirse, **yükler**' e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
- [Önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md)
- [Nasıl yapılır: Ürün bildirimi oluşturma](../deployment/how-to-create-a-product-manifest.md)
- [Nasıl yapılır: Paket bildirimi oluşturma](../deployment/how-to-create-a-package-manifest.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)
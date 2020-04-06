---
title: Özel Başlangıç Sayfalarını Dağıtma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712237"
---
# <a name="deploy-custom-start-pages"></a>Özel Başlangıç Sayfalarını Dağıtma

VSIX dağıtımını kullanarak veya dosyaları hedef bilgisayardaki doğru konumlara kopyalayarak özel Başlangıç Sayfaları dağıtabilirsiniz.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Başlangıç Sayfası proje şablonu kullanılarak VSIX dağıtımı

Başlangıç Sayfası proje şablonu kullanarak bir Başlangıç Sayfası oluşturduğunuzda ve projeyi oluşturduğunuzda, Visual Studio dağıtabileceğiniz bir *.vsix* dosyası oluşturur. Bir *.vsix* dosyasında Bir Başlangıç Sayfasını paketlemek, hedef kitlenize bağlı olarak dağıtım için aşağıdaki seçenekleri sunar:

- *.vsix* dosyasını bir ağ paylaşımına veya genel bir Web sitesine koyabilirsiniz. Birisi dosyayı açtığında, Başlangıç Sayfası otomatik olarak yüklenir.

- *.vsix* dosyasını [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Web sitesine yükleyebilirsiniz, böylece kullanıcılar Uzantısı **Yöneticisi'ni**kullanarak dosyayı yükleyebilirsiniz.

Başlangıç Sayfası proje şablonu, kopyayı değiştirebilmeniz ve orijinalini koruyabilmeniz için varsayılan Visual Studio Başlangıç Sayfasının bir kopyasını oluşturur.

Başlat Sayfası proje **şablonu'nu Uzantı Yöneticisi'ni** kullanarak veya Web sitesinden indirerek elde edebilirsiniz.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Başlangıç Sayfası proje şablonu kullanmadan VSIX dağıtımı
 Başarılı bir VSIX dağıtımı, VSIX kayıt işlemi ve **Uzantı Yöneticisi**tarafından tanınan klasörlere bir uzantı kurulmasını gerektirir. Başlangıç Sayfası proje şablonu zaten doğru klasörleri belirttiğinden, VSIX dağıtımı için bir uzantı paketi istediğinizde kullanmanızı öneririz. Ancak, şablonu kullanamayacağınız bir servis talebiniz varsa, kullanmadan bir VSIX dağıtımı oluşturabilirsiniz.

 Başlangıç Sayfası proje şablonu kullanmadan bir VSIX dağıtımı oluşturmak için, önce Başlangıç Sayfası için aşağıdaki iki şekilde bir *.vsix* dosyası oluşturun:

- Boş bir VSIX Projesine özel Başlangıç Sayfası dosyalarınızı ekleyerek. Daha fazla bilgi için [VSIX proje şablonuna](../extensibility/vsix-project-template.md)bakın.

- *Bir .vsix* dosyası el ile oluşturarak. *.vsix* dosyası nın el ile oluşturulması için:

   1. Yeni bir klasörde *extension.vsixmanifest* dosyasını ve *[Content_Types].xml* dosyasını oluşturun. Daha fazla bilgi için [vsix paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)bölümüne bakın.

   2. Windows Gezgini'nde, iki XML dosyasını içeren klasörü sağ tıklatın, **Gönder'i**tıklatın ve ardından Sıkıştırılmış (sıkıştırılmış) Klasörünü tıklatın. Dosya adı paketinizi yükler yeniden dağıtılabilir dosyanın adı olduğu *Filename.vsix*, ortaya çıkan *.zip* dosyası yeniden adlandırın.

Visual Studio'nun bir Başlangıç `Content Element` Sayfasını tanıması için, `"StartPage"` `CustomExtension Element` VSIX `Type` Bildirimi'nin bir özniteliği 'ne göre ayarlanmış bir özellik içermesi gerekir. VSIX dağıtımı kullanılarak yüklenen Bir Başlangıç Sayfası uzantısı **Başlangıç** seçenekleri sayfasında Ki **Başlangıç Sayfasını Özelleştir** listesinde **[Yüklü Uzantı]** *Uzantısı Adı*olarak görünür.

Başlangıç Sayfası paketinizde derlemeler varsa, Visual Studio başladığında kullanılabilmesi için bağlayıcı yol kaydı eklemeniz gerekir. Bunu yapmak için, paketinizin aşağıdaki bilgilere sahip bir *.pkgdef* dosyası içerdiğinden emin olun.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Tüm kullanıcılar için VSIX dağıtımı
 Varsayılan olarak, VSIX paketlerinde dağıtılan uzantılar yalnızca geçerli kullanıcı için yüklenir. Tüm Kullanıcılar dağıtımını oluşturarak hedef makinenin tüm kullanıcıları için Bir Başlangıç Sayfası yüklemesi yapabilirsiniz.

### <a name="to-create-an-all-users-deployment"></a>Tüm Kullanıcılar dağıtımı oluşturmak için

1. *uzantı.vsixmanifest* dosyasını kod görünümünde açın.

2. vsix `Identifier` bildiriminin öğesine, değeri `AllUsers` 'ne `true`sahip bir öğe ekleyin

    ```
    <AllUsers>true</AllUsers>
    ```

     Bu, vsix yükleyicisinin yönetici izinleri için istem deyip sonra dosyaları *\Common7\IDE\Extensions'a*yüklemesine neden olur.

3. *.pkgdef* dosyasını açın.

4. *MyStartPage.xaml* Başlangıç Sayfanızı içeren *.xaml* dosyasının adı olduğu aşağıdakileri ekleyerek HKLM altında varsayılan başlangıç sayfasını ayarlamak için *.pkgdef'i* değiştirin.

     [$RootKey$\Başlangıç Sayfası\Varsayılan]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Bu, Visual Studio'ya yeni Başlangıç Sayfası konumuna bakmasını söyler.

## <a name="file-copy-deployment"></a>Dosya kopyalama dağıtımı
 Özel bir Başlangıç Sayfası dağıtmak için *bir .vsix* dosyası oluşturmanız gerekmez. Bunun yerine, biçimlendirme ve destek dosyalarını doğrudan kullanıcının <em>\StartPages\* klasörüne kopyalayabilirsiniz. * Başlangıç seçenekleri sayfasındaki*Başlangıç Sayfasını Özelleştir,</em> * o klasördeki her *.xaml* dosyasını, yol ile birlikte listeler—örneğin, *%USERPROFILE%\My Documents\Visual Studio {version}\StartPages\\{File Name}.xaml*. **Startup** Başlangıç Sayfanızda özel derlemelere başvurular varsa, bunları kopyalamanız ve *\PrivateAssemblies\* klasörüne yapıştırmalısınız.

 Oluşturduğunuz Bir Başlangıç Sayfasını *.vsix* dosyasında paketlemeden dağıtmak için, dosyaları gerekli dizinlere koymanızı sağlayan bir toplu iş komut dosyası veya başka bir dağıtım teknolojisi gibi temel bir dosya kopyalama stratejisi kullanmanızı öneririz.

### <a name="to-manually-install-a-custom-start-page"></a>Özel bir Başlangıç Sayfasını el ile yüklemek için

1. Başlangıç Sayfası biçimlendirmesini içeren *.xaml* dosyasını derlemeler dışındaki destek dosyalarıyla birlikte kopyalayın ve kullanıcının *\StartPages\* klasörüne yapıştırın.

2. Başlangıç Sayfası derlemeler gerektiriyorsa, bunları kopyalayın ve *...... {Visual Studio yükleme klasörü}\Common7\IDE\PrivateAssemblies\\. \\*

3. **Başlangıç** seçenekleri sayfasındaki **Başlangıç Sayfasını Özelleştir** listesinde yeni Başlangıç Sayfasını seçin. Daha fazla bilgi için [Başlangıç Sayfasını Özelleştir'e](../ide/customizing-the-start-page-for-visual-studio.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Sayfasını Özelleştir](../ide/customizing-the-start-page-for-visual-studio.md)
- [Başlangıç Sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)

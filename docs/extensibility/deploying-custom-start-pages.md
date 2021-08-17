---
title: Özel başlangıç sayfalarını dağıtma | Microsoft Docs
description: VSıX dağıtımı kullanarak veya dosyaları hedef bilgisayardaki doğru konumlara kopyalayarak özel başlangıç sayfaları dağıtmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 07b757ab200bb3439fb82224ea1c20e3edb8ea16
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070388"
---
# <a name="deploy-custom-start-pages"></a>Özel başlangıç sayfalarını dağıtma

VSıX dağıtımı kullanarak veya dosyaları hedef bilgisayardaki doğru konumlara kopyalayarak özel başlangıç sayfaları dağıtabilirsiniz.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak VSıX dağıtımı

başlangıç sayfası proje şablonunu kullanarak bir başlangıç sayfası oluşturduğunuzda ve ardından projeyi derleyerek Visual Studio dağıtabileceğiniz bir *. vsix* dosyası oluşturur. Bir *. vsix* dosyasında başlangıç sayfası paketleme, hedeflenen dinleyiciye bağlı olarak dağıtım için aşağıdaki seçenekleri sağlar:

- *. Vsix* dosyasını bir ağ paylaşımında veya bir genel web sitesinde yerleştirebilirsiniz. Birisi dosyayı açtığında başlangıç sayfası otomatik olarak yüklenir.

- *. vsix* dosyasını, kullanıcıların **uzantı yöneticisi 'ni** kullanarak yükleyebilmeleri için [Visual Studio market](https://marketplace.visualstudio.com/) Web sitesine yükleyebilirsiniz.

başlangıç sayfası proje şablonu, kopyayı değiştirebilmeniz ve orijinali koruyabilmeniz için varsayılan Visual Studio başlangıç sayfasının bir kopyasını oluşturur.

Başlangıç sayfası proje şablonunu **Uzantı Yöneticisi** ' ni kullanarak veya Web sitesinden indirerek elde edebilirsiniz.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanmadan VSıX dağıtımı
 Başarılı bir VSıX dağıtımı, VSıX kayıt işlemi ve **Uzantı Yöneticisi** tarafından tanınan klasörlere bir uzantının yüklenmesini gerektirir. Başlangıç sayfası proje şablonu zaten doğru klasörleri belirttiğinden, VSıX dağıtımı için bir uzantı paketlemek istediğinizde bunu kullanmanızı öneririz. Ancak, şablonu kullanmadığınız bir servis talebine sahipseniz, kullanmadan bir VSıX dağıtımı oluşturabilirsiniz.

 Başlangıç sayfası proje şablonunu kullanmadan bir VSıX dağıtımı oluşturmak için önce bu iki şekilde başlangıç sayfası için bir *. VSIX* dosyası oluşturun:

- Özel başlangıç sayfası dosyalarınızı boş bir VSıX Project ekleyerek. Daha fazla bilgi için bkz. [VSIX proje şablonu](../extensibility/vsix-project-template.md).

- *. Vsix* dosyasını el ile oluşturun. El ile bir *. vsix* dosyası oluşturmak için:

   1. *Uzantısı. valtmanifest* dosyasını ve *[Content_Types] .xml* dosyasını yeni bir klasörde oluşturun. Daha fazla bilgi için bkz. [BIR VSIX paketinin Anatomı](../extensibility/anatomy-of-a-vsix-package.md).

   2. Windows gezgini ' nde, iki XML dosyasını içeren klasöre sağ tıklayın, **gönder ' e** tıklayın ve ardından sıkıştırılmış (daraltılmış) klasör ' e tıklayın. Elde edilen *.zip* dosyasını *filename. vsix* olarak yeniden adlandırın; burada filename, paketinizi yükleyen yeniden dağıtılabilir dosyanın adıdır.

bir başlangıç sayfasını tanıması Visual Studio için, `Content Element` vsıx bildiriminin, `CustomExtension Element` `Type` özniteliği olarak ayarlanmış olan bir öğesini içermesi gerekir `"StartPage"` . VSıX dağıtımı kullanılarak yüklenen bir başlangıç sayfası uzantısı, **Başlangıç** seçenekleri sayfasında **[yüklü uzantı]** *uzantı adı* olarak **Başlangıç sayfası Özelleştir** listesinde görünür.

başlangıç sayfası paketiniz derlemeleri içeriyorsa, Visual Studio başlatıldığında kullanılabilir olmaları için bağlama yolu kaydı eklemeniz gerekir. Bunu yapmak için, paketinizin aşağıdaki bilgileri içeren bir *. pkgdef* dosyası içerdiğinden emin olun.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Tüm kullanıcılar için VSıX dağıtımı
 Varsayılan olarak, VSıX paketlerinde dağıtılan uzantılar yalnızca geçerli kullanıcı için yüklenir. Bir All-Users dağıtımı oluşturarak hedef makinenin tüm kullanıcıları için başlangıç sayfası yüklemeyi yapabilirsiniz.

### <a name="to-create-an-all-users-deployment"></a>All-Users dağıtımı oluşturmak için

1. *Uzantı. valtmanifest* dosyasını kod görünümünde açın.

2. `Identifier`VSIX bildiriminin öğesinde, değeri olan bir `AllUsers` öğesi ekleyin `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     Bu, VSIX yükleyicisinin yönetici izinlerini sormasını ve sonra dosyaları *\Common7\IDE\Extensions*'e yüklemesini sağlar.

3. *. Pkgdef* dosyasını açın.

4. Şunları ekleyerek, *. pkgdef* öğesini HKLM altındaki varsayılan başlangıç sayfasını ayarlamak için değiştirin. burada *MyStartPage. xaml* , başlangıç sayfanızı içeren *. xaml* dosyasının adıdır.

     [$RootKey $ \StartPage\Default]

     "Uri" = "$PackageFolder $ \\ *MyStartPage. xaml*"

     bu, Visual Studio yeni başlangıç sayfası konumuna bakmasını söyler.

## <a name="file-copy-deployment"></a>Dosya kopyalama dağıtımı
 Özel bir başlangıç sayfası dağıtmak için bir *. vsix* dosyası oluşturmanız gerekmez. Bunun yerine, biçimlendirme ve destekleyici dosyaları doğrudan kullanıcının <em>\Startpages \* klasörüne kopyalayabilirsiniz. başlangıç seçenekleri sayfasındaki **başlangıç sayfasını özelleştir</em>* listesi  , bu klasördeki tüm *. xaml* dosyalarını (örneğin, *%userprofıle%\my Documents \ Visual Studio {version} \startpages \\ {file Name}. xaml*) listeler. Başlangıç sayfanız özel derlemelere başvurular içeriyorsa, bunları kopyalamanız ve * \PrivateAssemblies klasörüne yapıştırmanız gerekir \* .

 Oluşturduğunuz bir başlangıç sayfasını bir *. vsix* dosyasında paketlemeden dağıtmak için, bir toplu iş betiği veya dosyaları gerekli dizinlere yerleştirmenizi sağlayan başka bir dağıtım teknolojisi gibi temel bir dosya kopyalama stratejisi kullanmanızı öneririz.

### <a name="to-manually-install-a-custom-start-page"></a>Özel bir başlangıç sayfasını el ile yüklemek için

1. Başlangıç sayfası işaretlemesini içeren *. xaml* dosyasını derlemeler dışındaki destekleyici dosyalarla birlikte kopyalayın ve kullanıcının * \StartPages \* klasörüne yapıştırın.

2. Başlangıç sayfası derlemeler gerektiriyorsa, bunları kopyalayıp içine yapıştırın *... \\ {Visual Studio yükleme klasörü} \Common7\IDE\PrivateAssemblies \\*.

3. **Başlangıç** seçenekleri sayfasındaki **Başlangıç sayfasını Özelleştir** listesinde yeni başlangıç sayfasını seçin. Daha fazla bilgi için bkz. [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)
- [Başlangıç sayfasına kullanıcı denetimi Ekle](../extensibility/adding-user-control-to-the-start-page.md)

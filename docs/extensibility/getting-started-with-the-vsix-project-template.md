---
title: VSIX Proje Şablonu ile Başlarken | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711239"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX Project şablonu yla başlayın

Bir uzantı oluşturmak veya dağıtım için varolan bir uzantıyı paketlemek için VSIX Project şablonunu kullanabilirsiniz. VSIX Project şablonu hem Visual Basic hem de Visual C# sürümlerine sahiptir ve Visual Studio SDK'nın bir parçası olarak yüklenir.

 VSIX Project şablonu yalnızca uzantı ve aktardığı varlıklar hakkında bilgi içeren bir *source.extension.vsixmanifest* dosyasından oluşur.

 VSIX proje şablonu bulmak için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX Project şablonunu kullanarak Özel Proje Şablonu dağıtma

 Aşağıdaki adımlar, diğer geliştiricilerle paylaşabileceğiniz veya Visual Studio Galerisi'ne yükleyebileceğiniz bir proje şablonu paketlemek için VSIX projesinin nasıl kullanılacağını gösterir.

1. Proje şablonu oluşturun.

    1. Şablon oluşturmak için projeyi açın. Bu proje herhangi bir proje türünde olabilir.

    2. **Proje** menüsünde, **Dışa Aktarma Şablonu'nu**tıklatın. Sihirbazın adımlarını tamamlayın.

         *%USERPROFILE%\My Documents\Visual Studio {version}\Benim Dışa Aktarılan\\Şablonlarım'da bir* *.zip* dosyası oluşturulur.

2. Boş bir VSIX projesi oluşturun.

     **Dosya** > **Yeni** > **Proje'yi**seçin. Arama kutusuna "vsix" yazın ve **VSIX Project'in** **C#** veya **Visual Basic** sürümünü seçin.

3. .zip *.zip* dosyasını projeye ekleyin. Kopyasını **Çıktı Dizini özelliğine** `Copy Always`ayarla.

4. **Solution**Explorer'da, **VSIX Manifest Designer'da**açmak için *source.extension.vsixmanifest* dosyasını çift tıklatın ve ardından aşağıdaki değişiklikleri yapın:

    - Ürün **Adı** alanını **Proje Şablonum**olarak ayarlayın.

    - Ürün **Kimliği** alanını **MyProjectTemplate**olarak ayarlayın - 1 .

    - **Yazar** alanını **Fabrikam'a**ayarlayın.

    - **Açıklama** alanını **proje şablonuma**ayarlayın.

    - **Varlıklar** bölümünde, bir **Microsoft.VisualStudio.ProjectTemplate** türü ekleyin ve *.zip* dosyasının adına yolunu ayarlayın.

5. *Source.extension.vsixmanifest* dosyasını kaydedin ve kapatın.

6. Projeyi derleyin.

7. Çıktı dizininde *.vsix* dosyasını çift tıklatın.

8. Bir **VSIX Yükleyici** ileti kutusu görüntülenir. Uzantıyı yüklemek için yönergeleri izleyin.

9. Visual Studio'yı kapatın ve yeniden açın.

::: moniker range="vs-2017"

10. **Uzantılar ve Güncelleştirmeler** **(Araçlar** menüsünde) ve **Şablonlar** kategorisini seçin. Kullanılabilir uzantılardan biri **Proje Şablonum**olmalıdır.

::: moniker-end

::: moniker range=">=vs-2019"

10. **Uzantıları Yönet'i** **(Uzantılar** menüsünde) seçin ve **Şablonlar** kategorisini seçin. Kullanılabilir uzantılardan biri **Proje Şablonum**olmalıdır.

::: moniker-end

11. Yeni proje şablonu, **Özgün proje** şablonuyla aynı yerde yeni proje iletişim kutusunda görünür. Örneğin, Visual Basic konsol uygulamasından **VB Konsol** adında bir şablon oluşturduysanız, **VB Konsolu** Visual Basic **Console Application** şablonuyla aynı bölmede görünür.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni Proje İletişim kutusunda şablonun konumunu belirtmek için

1. Şablon klasörleri *{Visual Studio Installation Path}\Common7\IDE\ProjectTemplates* ve *{Visual Studio Installation Path}\Common7\IDE\ItemTemplates* dizinde bulunur. **Yeni Proje** iletişim kutusundaki üst düzey bölümlerin adları şablon klasörlerinin adlarıyla tam olarak eşleşmiyor. Farklı oldukları durumlarda, şablon klasörünün adını kullanın.

    *.vsix* dosya uzantısını *.zip*olarak değiştirin ve sonra dosyayı açın.

2. **Şablonun** görünmesi gereken Yeni Proje iletişim kutusunun bölümüyle aynı ada sahip yeni bir klasör oluşturun.

3. Şablon bir alt bölümde görünecekse, aynı adı taşıyan bir alt klasör oluşturun.

4. Şablon *.zip* dosyasını yeni klasöre taşıyın.

5. *.zip* uzantısını *.vsix olarak değiştirin.*

6. VSIX manifestosunun açın.

7. VSIX bildiriminde, şablonun **Varlık** yolunu şablon dosyasını içeren dizin ağacının köküne işaret etmek için güncelleştirin. Örneğin, şablon *\CSharp\Windows'daise,* başvuru *\CSharp'ı*işaret etmelidir.

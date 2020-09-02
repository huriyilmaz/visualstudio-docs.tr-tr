---
title: VSıX proje şablonu ile çalışmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc3f461c9e7dbdea1fd8481594292a0a247d2173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204295"
---
# <a name="getting-started-with-the-vsix-project-template"></a>VSIX Proje Şablonunu Kullanmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uzantı oluşturmak veya var olan bir uzantıyı dağıtım için paketlemek üzere VSıX proje şablonunu kullanabilirsiniz. VSıX proje şablonunda hem Visual Basic hem de Visual C# sürümleri vardır ve Visual Studio SDK 'sının bir parçası olarak yüklenir.  
  
 VSıX proje şablonu, uzantısı ve geldiği varlıklar hakkında bilgi içeren bir Source. Extension. valtmanifest dosyasından oluşur.  
  
 VSıX proje şablonunu bulmak için Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>VSıX proje şablonunu kullanarak özel proje şablonu dağıtma  
 Aşağıdaki adımlarda, diğer geliştiricilerle paylaşabileceğiniz veya Visual Studio Galerisine yükleyebileceğiniz bir proje şablonunu paketlemek için VSıX projesinin nasıl kullanılacağı gösterilmektedir.  
  
1. Proje şablonu oluşturun.  
  
    1. Şablonun oluşturulacağı projeyi açın. Bu proje herhangi bir proje türünde olabilir.  
  
    2. **Dosya** menüsünde, **şablonu dışarı aktar**' a tıklayın. Sihirbazın adımlarını izleyin.  
  
         Bir. zip dosyası,%USERPROFILE%\My, Studio *\<version>* \Ihraç şablonları 'nda oluşturulur \\ .  
  
2. Boş bir VSıX projesi oluşturun.  
  
     **Dosya** menüsünde **Yeni** ' ye ve ardından **Proje**' ye tıklayın. **Visual Basic** veya **Visual C#** seçeneklerinden birini belirleyin. Seçili düğüm altında **genişletilebilirlik**' i ve ardından **VSIX projesi**' ni seçin.  
  
3. . Zip dosyasını projeye ekleyin. **Çıkış Dizinine Kopyala** özelliğini olarak ayarlayın `Copy Always` .  
  
4. **Çözüm Gezgini**, `source.extension.vsixmanifest` dosyayı **VSIX bildirim tasarımcısında**açmak için dosyaya çift tıklayın ve ardından aşağıdaki değişiklikleri yapın:  
  
    - **Ürün adı** alanını **Proje Şablonum**olarak ayarlayın.  
  
    - **Ürün kimliği** alanını **myprojecttemplate-1**olarak ayarlayın.  
  
    - **Yazar** alanını **fabrikam**olarak ayarlayın.  
  
    - **Açıklama** alanını **Proje Şablonum**olarak ayarlayın.  
  
    - **Varlıklar** bölümünde, bir **Microsoft. VisualStudio. ProjectTemplate** türü ekleyin ve yolunu. zip dosyasının adı olarak ayarlayın.  
  
5. Source. Extension. valtmanifest dosyasını kaydedin ve kapatın.  
  
6. Projeyi derleyin.  
  
7. Çıktı dizininde,. vsix dosyasına çift tıklayın.  
  
8. **VSIX yükleyici** ileti kutusu görüntülenir. Uzantıyı yüklemek için yönergeleri izleyin.  
  
9. Visual Studio 'Yu kapatın ve yeniden açın.  
  
10. **Uzantılar ve güncelleştirmeler** ' i seçin ( **Araçlar** menüsünde) ve **Şablonlar** kategorisini seçin. Kullanılabilir uzantılardan biri **Proje Şablonum**olmalıdır.  
  
11. Yeni proje şablonu, **Yeni proje** iletişim kutusunda orijinal proje şablonuyla aynı yerde görüntülenir. Örneğin, bir Visual Basic konsol uygulamasından **vb konsolu** adlı bir şablon oluşturduysanız, **vb konsolu** Visual Basic **Konsolu uygulama** şablonuyla aynı bölmede görünür.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Yeni proje Iletişim kutusunda şablonun konumunu belirtmek için  
  
1. Şablon klasörleri *Visual Studio yükleme yolu*\Common7\IDE\ProjectTemplates ve *Visual Studio yükleme yolu*\Common7\IDE\ItemTemplates dizinlerinde bulunur. Yeni proje iletişim kutusundaki en üst düzey bölümlerin adları, şablon klasörlerinin adlarıyla tam olarak eşleşmez. Nerede farklıysa, şablon klasörünün adını kullanın.  
  
     . Vsix dosya uzantısını. zip olarak değiştirin ve ardından dosyayı açın.  
  
2. Şablonun içinde görünmesi gereken yeni proje iletişim kutusunun bölümüyle aynı ada sahip yeni bir klasör oluşturun.  
  
3. Şablon bir alt bölümde görünürse, aynı ada sahip bir alt klasör oluşturun.  
  
4. Template. zip dosyasını yeni klasöre taşıyın.  
  
5. . Zip uzantısını. vsix olarak değiştirin.  
  
6. VSıX bildirimini açın.  
  
7. VSıX bildiriminde, şablonun **varlık** yolunu, şablon dosyasını içeren dizin ağacının köküne işaret eden bir şekilde güncelleştirin. Örneğin, şablon \CSharp\Windows ise, başvuru \Csharp' a işaret etmelidir.

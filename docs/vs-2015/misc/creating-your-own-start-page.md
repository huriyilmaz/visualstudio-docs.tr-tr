---
title: Kendi başlangıç sayfanızı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: fba7f1e0801b6f977d47b13af025538f5d2fe031
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850988"
---
# <a name="creating-your-own-start-page"></a>Kendi başlangıç sayfanızı oluşturma
Başlangıç sayfası proje şablonunu kullanarak ya da boş bir başlangıç sayfası oluşturarak özel bir başlangıç sayfası oluşturabilirsiniz.  
  
 XAML Tasarımcısı, Visual Studio uygulama modelindeki bağımlılıklar nedeniyle özel başlangıç sayfalarının tamamen doğru görsel sunumlarını sağlamayabilir.  
  
## <a name="using-the-project-template"></a>Proje şablonunu kullanma  
 Başlangıç sayfası proje şablonu, Visual Studio başlangıç sayfasının tamamen bir kopyası olan bir başlangıç sayfası projesi oluşturur. Daha sonra başlangıç sayfasını belirtimlerinize göre düzenleyebilirsiniz.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak özel bir başlangıç sayfası oluşturmak için  
  
1. Visual Studio galerisinden [Başlangıç sayfası proje şablonunu](https://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) indirin ve yükleyin.  
  
    > [!WARNING]
    > Bu sırada, Visual Studio 2010 başlangıç sayfası proje şablonu yükseltilmemiştir. Bu şablonu yükseltme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio özel başlangıç sayfasını yükseltme](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Şablonu yükledikten sonra, ile yeni bir başlangıç sayfası projesi oluşturun.  
  
3. Yeni proje iletişim kutusunun sol bölmesinde, **yüklü şablonlar**altında **diğer proje türleri** düğümünü genişletin ve ardından **genişletilebilirlik**' e tıklayın.  
  
4. Orta bölmede **özel başlangıç sayfası**' nı tıklatın ve sonra projenizi adlandırın ve **Tamam**' ı tıklatın.  
  
     Visual Studio, Visual Studio başlangıç sayfasının tamamen bir kopyası olan bir başlangıç sayfası projesi oluşturur.  
  
5. **Çözüm Gezgini**, **StartPage. xaml**' yi açın.  
  
6. StartPage. xaml 'yi düzenleyin.  
  
     Özel başlangıç sayfası yüklüyken, Visual Studio 'nun deneysel bir örneğini açmak için F5 'e basarak çalışmanızı görüntüleyebilirsiniz.  
  
## <a name="creating-a-blank-start-page"></a>Boş bir başlangıç sayfası oluşturma  
 Boş bir başlangıç sayfası oluşturmanın en kolay yolu, başlangıç sayfası proje şablonunu kullanmaktır ve sonra içeriği kaldırır.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Başlangıç sayfası proje şablonunu kullanarak boş bir başlangıç sayfası oluşturmak için  
  
1. Önceki yordamda açıklandığı gibi, başlangıç sayfası proje şablonunu kullanarak bir başlangıç sayfası projesi oluşturun.  
  
2. StartPage. xaml ' i açın.  
  
3. . Xaml dosyanız aşağıdaki örneğe benzer şekilde, yalnızca dış XML öğelerinden ve kapsayan Izgara <xref:System.Windows.Controls.Grid> öğesini bırakarak tüm sayfa içeriğini kaldırın.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Kullanmayı düşündüğünüz tüm destekleyici dosyaları kaldırın.  
  
    Dağıtım amaçlarıyla. vsix ve. pkgdef dosyalarını tutmanız gerekir.  
  
   Alternatif olarak, Visual Studio tarafından tanınması için doğru etiket yapısına sahip bir XAML dosyası oluşturarak boş bir başlangıç sayfası oluşturabilirsiniz. Daha sonra istediğiniz görünüm ve işlevselliği almak için biçimlendirme ve arka plan kodu ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Özel başlangıç sayfasını test etme ve uygulama  
 Birincil örneği, kilitlenmediğinden emin olana kadar özel başlangıç sayfasını çalıştıracak şekilde ayarlamayın. Özel başlangıç sayfanızı test ettiğinizde, Visual Studio 'nun birincil örneğindeki bu yordamın son üç adımını yineleyerek uygulamanızı sisteminize uygulayabilirsiniz.  
  
#### <a name="to-test-a-custom-start-page"></a>Özel bir başlangıç sayfasını test etmek için  
  
1. F5 tuşuna basın.  
  
    Visual Studio 'nun deneysel örneği yeni başlangıç sayfası yüklenmiş ancak seçilmemiş olarak açılır.  
  
2. Visual Studio 'nun deneysel örneğinde, **Araçlar** menüsünde **Seçenekler**' e tıklayın.  
  
3. **Seçenekler** iletişim kutusunda, **ortam**altında **Başlangıç**' ı seçin. Ardından, **Başlangıç sayfasını Özelleştir** listesinden. xaml dosyanızı seçin ve **Tamam**' a tıklayın.  
  
4. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.  
  
    Çalışma başlangıcı sayfası görüntülenir. Deneysel örneği kapatmanız, değiştirilen dosyaları yeniden kopyalamanız ve ardından yeni değişiklikleri görmek için deneysel örneği yeniden açmanız gerekir.  
  
   . Vsix dosyasını bin\Debug dizininizden [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine veya başka bir Web sitesine veya intranet paylaşımıyla karşıya yükleyerek özel başlangıç sayfanızı paylaşabilirsiniz. Daha fazla bilgi için bkz. [özel başlangıç sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç sayfasını özelleştirme](../ide/customizing-the-start-page-for-visual-studio.md)   
 [İzlenecek Yol: Başlangıç Sayfasına Özel XAML Ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)

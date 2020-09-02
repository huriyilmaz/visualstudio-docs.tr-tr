---
title: Yalıtılmış Kabuğu genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea55039de769598b26868727a93cfa11726e4838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799323"
---
# <a name="extending-the-isolated-shell"></a>Yalıtılmış Kabuğu Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalıtılmış Kabuk uygulamanıza bir VSPackage, Managed Extensibility Framework (MEF) bileşen bölümü veya genel VSıX projesi ekleyerek Visual Studio yalıtılmış kabuğunu genişletebilirsiniz.  
  
> [!NOTE]
> Aşağıdaki adımlarda, Visual Studio Kabuğu yalıtılmış proje şablonunu kullanarak temel yalıtılmış bir kabuk uygulaması oluşturmuş olursunuz. Bu proje şablonu hakkında daha fazla bilgi için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio paketi proje şablonu konumları  
 Visual Studio paketi proje şablonu, **Yeni proje** iletişim kutusunda üç farklı konumda bulunabilir:  
  
1. **Visual Basic**, **genişletilebilirlik**altında. Projenin varsayılan dili Visual Basic.  
  
2. **Visual C#**' ın altında **genişletilebilirlik**. Projenin varsayılan dili C# ' dir.  
  
3. **Diğer proje türleri**altında **genişletilebilirlik**. Projenin varsayılan dili C++ ' dır.  
  
## <a name="adding-a-vspackage"></a>VSPackage ekleme  
 Yalıtılmış Kabuk uygulamanıza VSPackage ekleyebilirsiniz. Aşağıdaki adımlarda menü komutları ekleyen bir işlemin nasıl oluşturulacağı gösterilmektedir.  
  
#### <a name="to-add-a-new-vspackage"></a>Yeni bir VSPackage eklemek için  
  
1. Adlı bir Visual Studio paket projesi ekleyin `MenuCommandsPackage` .  
  
2. Sihirbazın **temel VSPackage bilgileri** sayfasında, **Şirket adı** ' nı `Fabrikam` ve **VSPackage adı** ' nı olarak ayarlayın `FabrikamMenuCommands` . **İleri** düğmesini seçin.  
  
3. Sonraki sayfada **menü komutu** ' nu ve ardından **İleri**' yi seçin.  
  
4. Sonraki sayfada, **komut adını** `Fabrikam Command` ve **komut kimliğini** olarak ayarlayın `cmdidFabrikamCommand` ve ardından **İleri**' yi seçin.  
  
5. **Test projesi seçeneklerini seç** sayfasında, test seçeneklerini temizleyin ve ardından **son** düğmesini seçin.  
  
6. ShellExtensionsVSIX projesinde, Source. Extension. valtmanifest dosyasını açın.  
  
     **Varlıklar** bölümü VSShellStub. AboutBoxPackage projesi için bir giriş içermelidir.  
  
7. **Yeni** düğmesini seçin.  
  
8. **Yeni varlık Ekle** penceresinde, **tür** listesinde, **Microsoft. VisualStudio. VSPackage**' ı seçin.  
  
9. **Kaynak** listesinde, **geçerli çözümdeki bir projenin** seçildiğinden emin olun. **Proje** liste kutusunda **MenuCommandsPackage**' ı seçin.  
  
10. Dosyayı kaydedin ve kapatın.  
  
11. Çözümü yeniden derleyin ve yalıtılmış kabukta hata ayıklamayı başlatın.  
  
12. Menü çubuğunda **Araçlar** menüsünü ve ardından **fabrikam komutu**' nı seçin.  
  
     İleti kutusu görünmelidir.  
  
13. Uygulamada hata ayıklamayı durdurun.  
  
## <a name="adding-a-mef-component-part"></a>MEF bileşen bölümü ekleme  
 Aşağıdaki adımlarda, yalıtılmış Kabuk uygulamanıza bir MEF bileşeni bölümünün nasıl ekleneceği gösterilmektedir.  
  
#### <a name="to-add-a-mef-component"></a>MEF bileşeni eklemek için  
  
1. **Yeni Proje Ekle** iletişim kutusunda, **Visual C#**, **genişletilebilirlik**altında, bir proje eklemek için **Düzenleyici kenar boşluğu** şablonunu kullanın. Bunu, `ShellEditorMargin` olarak adlandırın.  
  
2. ShellExtensionsVSIX projesinde, kod görünümünde değil Tasarım görünümü kaynak. Extension. valtmanifest dosyasını açın.  
  
3. `Asset`Bölümünde **İçerik Ekle**' yi seçin.  
  
4. **Yeni varlık Ekle** penceresinde, **tür** listesinde, **Microsoft. VisualStudio. MefComponent**öğesini seçin.  
  
5. **Kaynak** listesinde, **geçerli çözümdeki bir projenin** seçildiğinden emin olun. **Proje** liste kutusunda **Sheltaditormargin**' ı seçin.  
  
6. Dosyayı kaydedin ve kapatın.  
  
7. Çözümü yeniden derleyin ve yalıtılmış kabukta hata ayıklamayı başlatın.  
  
8. Bir metin dosyası açın.  
  
     "Hello World!" sözcüklerini içeren yeşil bir kenar boşluğu metin dosyası penceresinin alt kısmında görüntülenmelidir.  
  
9. Uygulamada hata ayıklamayı durdurun.  
  
## <a name="adding-a-generic-vsix-project"></a>Genel VSıX projesi ekleme  
  
#### <a name="to-add-a-generic-vsix-project"></a>Genel VSıX projesi eklemek için  
  
1. **Yeni Proje Ekle** iletişim kutusunda, **Visual C#**, **genişletilebilirlik**altında bir proje eklemek için **valtıproje** şablonunu kullanın. Bunu, `EmptyVSIX` olarak adlandırın.  
  
2. ShellExtensionsVSIX projesinde, kod görünümünde değil Tasarım görünümü kaynak. Extensions. valtmanifest dosyasını açın.  
  
3. `Assets`Bölümünde **Yeni**' yi seçin.  
  
4. **Yeni varlık Ekle** penceresindeki **tür** listesinden eklemek istediğiniz içerik türünü seçin.  
  
5. **Kaynak**bölümünde, **Geçerli çözümde bir proje** seçeneğinin seçildiğinden emin olun. Liste kutusunda VSıX projenizin adını seçin.  
  
6. Dosyayı kaydedin ve kapatın.  
  
7. Bu proje derlenmiş kod içeriyorsa, derlemeyi çıkışa dahil etmek için projeyi düzenlemeniz gerekir.  
  
    1. VSıX projesini kaldırın ve proje dosyasını açın.  
  
    2. İlk `<PropertyGroup>` blokta değerini `<CopyBuildOutputToOutputDirectory>` olarak değiştirin `true` .  
  
    3. Projeyi kaydedin ve yeniden yükleyin.  
  
8. Çözümü derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Temel Yalıtılmış Kabuk Uygulaması Oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

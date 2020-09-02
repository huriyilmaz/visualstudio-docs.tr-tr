---
title: Düzenleyici öğe şablonuyla uzantı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ccdd87d44ee90c925992f4d7b997c9bbe09684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834052"
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyiciyle sınıflandırmalar, donmanlar ve kenar boşlukları ekleyen temel Düzenleyici uzantıları oluşturmak için Visual Studio SDK 'sında bulunan öğe şablonlarını kullanabilirsiniz. Düzenleyici öğe şablonları, Visual C# veya Visual Basic VSıX projeleri için kullanılabilir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Sınıflandırıcı uzantısı oluşturma  
 Düzenleyici sınıflandırıcı öğe şablonu, herhangi bir metin dosyasındaki uygun metni (Bu durumda, her şey) renkeden bir düzenleyici sınıflandırıcı oluşturur.  
  
1. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **genişletilebilirlik**' e tıklayın. **Şablonlar** bölmesinde **VSIX projesi**' ni seçin. **Ad** kutusuna `TestClassifier` yazın. **Tamam**’a tıklayın.  
  
2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Düzenleyici sınıflandırıcı**' yı seçin. Varsayılan dosya adını (EditorClassifier1.cs) bırakın.  
  
3. Aşağıdaki gibi üç kod dosyası vardır:  
  
    - EditorClassifier1.cs, `EditorClassifier1` sınıfını içerir.  
  
    - EditorClassifier1ClassificationDefinition.cs, `OEditorClassifier1ClassificationDefinition` sınıfını içerir.  
  
    - EditorClassifier1Format.cs, `EditorClassifier1Format`  sınıfını içerir.  
  
    - EditorClassifier1Provider.cs, `EditorClassifier1Provider` sınıfını içerir.  
  
4. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görüntülenir.  
  
     Bir metin dosyası açarsanız, tüm metin mor arka plana göre altı çizili olur.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Metin göreli kenarlığı uzantısı oluşturma  
 Düzenleyici metni kenarlığı şablonu, kırmızı bir ana hat ve mavi arka plana sahip bir kutu kullanarak, ' a ' metin karakterinin tüm örneklerini süsleyerek metin göreli bir kenarlığı oluşturur. Metin göreli olarak değişir çünkü kutu, taşındıklarında veya yeniden biçimlendirildiklerinde bile her zaman ' a ' karakterlerinin bulunduğu yerlerdir.  
  
1. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **genişletilebilirlik**' e tıklayın. **Şablonlar** bölmesinde **VSIX projesi**' ni seçin. **Ad** kutusuna `TestAdornment` yazın. **Tamam**’a tıklayın.  
  
2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Düzenleyici metni kenarlığı**' nı seçin. Varsayılan dosya adını (TextAdornment1.cs/vb) bırakın.  
  
3. Aşağıdaki gibi iki kod dosyası vardır:  
  
    - TextAdornment1.cs, `TextAdornment1` sınıfını içerir.  
  
    - extAdornment1TextViewCreationListener.cs, `TextAdornment1TextViewCreationListener` sınıfını içerir.  
  
4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir. Bir metin dosyası açarsanız, metindeki tüm ' a ' karakterleri mavi bir arka planda kırmızı renkle gösterilir.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Görünüm penceresi göreli kenarlığı uzantısı oluşturma  
 Düzenleyici Görünüm penceresi kenarlığı şablonu, görünüm penceresinin sağ üst köşesine kırmızı bir ana hat içeren bir mor kutu ekleyen Görünüm penceresi ile göreli bir kenarlığı oluşturur.  
  
> [!NOTE]
> *Görünüm penceresi* , şu anda görüntülenen metin görünümünün alanıdır.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Düzenleyici Görünüm penceresi kenarlığı şablonunu kullanarak bir görünüm penceresi kenarlığı uzantısı oluşturmak için  
  
1. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **genişletilebilirlik**' e tıklayın. **Şablonlar** bölmesinde **VSIX projesi**' ni seçin. **Ad** kutusuna `ViewportAdornment` yazın. **Tamam**’a tıklayın.  
  
2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Düzenleyici Görünüm penceresi kenarlığı**' ni seçin. Varsayılan dosya adını (ViewportAdornment1.cs/vb) bırakın.  
  
3. Aşağıdaki gibi iki kod dosyası vardır:  
  
    - ViewportAdornment1.cs, `ViewportAdornment1` sınıfını içerir.  
  
    - ViewportAdornment1TextViewCreationListener.cs, `ViewportAdornment1TextViewCreationListener` sınıfını içerir  
  
4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir. Yeni bir metin dosyası oluşturursanız, görünüm penceresinin sağ üst köşesinde kırmızı bir ana hat içeren bir menekşe kutusu görüntülenir.  
  
## <a name="creating-a-margin-extension"></a>Kenar boşluğu uzantısı oluşturma  
 Düzenleyici kenar boşluğu şablonu, "Hello World!" keliimiyle birlikte görünen yeşil bir kenar boşluğu oluşturur yatay kaydırma çubuğunun altında.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Düzenleyici kenar boşluğu şablonunu kullanarak bir kenar boşluğu uzantısı oluşturmak için  
  
1. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **genişletilebilirlik**' e tıklayın. **Şablonlar** bölmesinde **VSIX projesi**' ni seçin. **Ad** kutusuna `MarginExtension` yazın. **Tamam**’a tıklayın.  
  
2. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. Visual C# **genişletilebilirlik** düğümüne gidin ve **Düzenleyici Görünüm penceresi kenarlığı**' ni seçin. Varsayılan dosya adını (EditorMargin1.cs/vb) bırakın.  
  
3. Aşağıdaki gibi iki kod dosyası vardır:  
  
    - EditorMargin1.cs, `EditorMargin1` sınıfını içerir.  
  
    - EditorMargin1Factory.cs, `EditorMargin1Factory` sınıfını içerir.  
  
4. Bu projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir. Bir metin dosyası açarsanız, yatay kaydırma çubuğunun altında "Hello EditorMargin1" sözcüklerini içeren yeşil bir kenar boşluğu görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

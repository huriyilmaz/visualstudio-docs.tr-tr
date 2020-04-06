---
title: Düzenleyici Öğe Şablonuyla Uzantı Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739511"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Düzenleyici öğesi şablonuyla uzantı oluşturma
Visual Studio SDK'da bulunan öğe şablonlarını kullanarak düzenleyiciye sınıflandırıcılar, süsler ve kenar boşlukları ekleyen temel düzenleyici uzantıları oluşturabilirsiniz. Düzenleyici öğesi şablonları Visual C# veya Visual Basic VSIX projeleri için kullanılabilir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-classifier-extension"></a>Sınıflandırıcı uzantısı oluşturma
 Düzenleyici Sınıflandırıcı öğesi şablonu, herhangi bir metin dosyasında uygun metni (bu durumda, her şeyi) renklendiren bir düzenleyici sınıflandırıcı oluşturur.

1. Yeni **Proje** iletişim kutusunda, **Visual C#** veya **Visual Basic'i** genişletin ve ardından **Genişletilebilirliği**tıklatın. **Şablonlar** bölmesinde **VSIX Project'i**seçin. **Ad** kutusuna `TestClassifier` yazın. **Tamam**'a tıklayın.

2. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Visual C# **Genişletilebilirlik** düğümüne gidin ve **Düzenleyici Sınıflandırıcı'yı**seçin. Varsayılan dosya adını *(EditorClassifier1.cs)* bırakın.

3. Aşağıdaki gibi dört kod dosyası vardır:

    - *EditorClassifier1.cs* `EditorClassifier1` sınıfı içerir.

    - *EditorClassifier1ClassificationDefinition.cs* `EditorClassifier1ClassificationDefinition` sınıfı içerir.

    - *EditorClassifier1Format.cs* `EditorClassifier1Format` sınıfı içerir.

    - *EditorClassifier1Provider.cs* `EditorClassifier1Provider` sınıfı içerir.

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği ortaya çıkar.

     Bir metin dosyasını açarsanız, tüm metin menekşe arka plan aleyhine altı çizilir.

## <a name="create-a-text-relative-adornment-extension"></a>Metin göreli süsleme uzantısı oluşturma
 Düzenleyici Metin Süsleme şablonu, kırmızı anahat ve mavi arka plan içeren bir kutu kullanarak metin karakterinin tüm örneklerini 'a' olarak süsleyen bir metin göreli süs oluşturur. Kutu her zaman 'a' karakterleri, taşınmış veya yeniden biçimlendirildiğinde bile, her zaman yerle bir olduğundan metin görecelidir.

1. Yeni **Proje** iletişim kutusunda, **Visual C#** veya **Visual Basic'i** genişletin ve ardından **Genişletilebilirliği**tıklatın. **Şablonlar** bölmesinde **VSIX Project'i**seçin. **Ad** kutusuna `TestAdornment` yazın. **Tamam**'a tıklayın.

2. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Visual C# **Genişletilebilirlik** düğümüne gidin ve **Editör Metin Süsleme'yi**seçin. Varsayılan dosya adını *(TextAdornment1.cs/vb)* bırakın.

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *TextAdornment1.cs* `TextAdornment1` sınıfı içerir.

    - *TextAdornment1TextViewCreationListener.cs* `TextAdornment1TextViewCreationListener` sınıfı içerir.

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir. Bir metin dosyasını açarsanız, metindeki tüm 'a' karakterleri mavi arka plan aleyhine kırmızı renkte özetlenir.

## <a name="create-a-viewport-relative-adornment-extension"></a>Viewport göreli süsleme uzantısı oluşturma
 Editor Viewport Süsleme şablonu, viewport'un sağ üst köşesine kırmızı bir anahat içeren bir mor kutu ekleyen bir viewport göreli süsleme oluşturur.

> [!NOTE]
> **Görünüm alanı,** metin görünümünün şu anda görüntülenen alanıdır.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Editor Viewport Süsleme şablonu kullanarak bir viewport süsleme uzantısı oluşturmak için

1. Yeni **Proje** iletişim kutusunda, **Visual C#** veya **Visual Basic'i** genişletin ve ardından **Genişletilebilirliği**tıklatın. **Şablonlar** bölmesinde **VSIX Project'i**seçin. **Ad** kutusuna `ViewportAdornment` yazın. **Tamam**'a tıklayın.

2. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Visual C# **Genişletilebilirlik** düğümüne gidin ve **Editor Viewport Adornment'i**seçin. Varsayılan dosya adını *(ViewportAdornment1.cs/vb)* bırakın.

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *ViewportAdornment1.cs* `ViewportAdornment1` sınıfı içerir.

    - *ViewportAdornment1TextViewCreationListener.cs* `ViewportAdornment1TextViewCreationListener` sınıfı içerir

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir. Yeni bir metin dosyası oluşturursanız, görünüm portunun sağ üst köşesinde kırmızı anahat içeren bir mor kutu görüntülenir.

## <a name="create-a-margin-extension"></a>Kenar boşluğu uzantısı oluşturma
 Editör Marjı şablonu * Merhaba dünya kelimeleri ile birlikte görünen yeşil bir kenar boşluğu*oluşturur!* yatay kaydırma çubuğunun altında.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Düzenleyici Kenar Boşluğu şablonu kullanarak bir kenar boşluğu uzantısı oluşturmak için

1. Yeni **Proje** iletişim kutusunda, **Visual C#** veya **Visual Basic'i** genişletin ve ardından **Genişletilebilirliği**tıklatın. **Şablonlar** bölmesinde **VSIX Project'i**seçin. **Ad** kutusuna `MarginExtension` yazın. **Tamam**'a tıklayın.

2. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Visual C# **Genişletilebilirlik** düğümüne gidin ve **Düzenleyici Kenar Boşluğu'nu**seçin. Varsayılan dosya adını (EditorMargin1.cs/vb) bırakın.

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *EditorMargin1.cs* `EditorMargin1` sınıfı içerir.

    - *EditorMargin1Factory.cs* `EditorMargin1Factory` sınıfı içerir.

4. Bu projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir. Bir metin dosyasını açarsanız, Yatay kaydırma çubuğunun altında **Hello EditorMargin1** sözcükleri olan yeşil bir kenar boşluğu görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve editör uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)

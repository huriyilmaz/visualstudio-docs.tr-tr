---
title: Düzenleyici Öğesi Şablonu şablonuyla uzantı | Microsoft Docs
description: Visual Studio SDK'sı içinde öğe şablonlarını kullanarak düzenleyiciye sınıflandırıcı, donatma ve kenar boşlukları ekleyen temel düzenleyici uzantıları oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c75d0a86d92c88c850e3b8250e3ac3551a1b75b475db9032f282355711f74db2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263003"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Düzenleyici öğesi şablonuyla uzantı oluşturma
Visual Studio SDK'sine dahil edilen öğe şablonlarını kullanarak düzenleyiciye sınıflandırıcı, donatma ve kenar boşlukları ekleyen temel düzenleyici uzantıları oluşturabilirsiniz. Düzenleyici öğesi şablonları Visual C# veya VSIX Visual Basic kullanılabilir.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-classifier-extension"></a>Sınıflandırıcı uzantısı oluşturma
 Düzenleyici Sınıflandırıcı öğe şablonu, herhangi bir metin dosyasında uygun metni (bu durumda her şeyi) renkletiren bir düzenleyici sınıflandırıcısı oluşturur.

1. Yeni **Project** iletişim kutusunda **Visual C#** veya  Visual Basic'ı genişletin ve ardından **Genişletilebilirlik'e tıklayın.** Şablonlar **bölmesinde** **VSIX'i seçin ve Project.** **Ad** kutusuna `TestClassifier` yazın. **Tamam**'a tıklayın.

2. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Visual C# **Genişletilebilirlik düğümüne gidin ve** Düzenleyici Sınıflandırıcı'ya **gidin.** Varsayılan dosya adını (*EditorClassifier1.cs ) bırakın.*

3. Aşağıdaki gibi dört kod dosyası vardır:

    - *EditorClassifier1.cs* sınıfı `EditorClassifier1` içerir.

    - *EditorClassifier1ClassificationDefinition.cs* sınıfı `EditorClassifier1ClassificationDefinition` içerir.

    - *EditorClassifier1Format.cs* sınıfı `EditorClassifier1Format`  içerir.

    - *EditorClassifier1Provider.cs* sınıfı `EditorClassifier1Provider` içerir.

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek Visual Studio görünür.

     Bir metin dosyası açarsanız, tüm metin arka planda altı çizili olur.

## <a name="create-a-text-relative-adornment-extension"></a>Metin göreli donatma uzantısı oluşturma
 Düzenleyici Metin Donatma şablonu, kırmızı ana hat ve mavi arka plan olan bir kutu kullanarak 'a' metin karakterinin tüm örneklerini donatan metin göreli bir donatma oluşturur. Taşınsa veya yeniden biçimlendirildiklerde bile kutu her zaman 'a' karakterlerini yer paylaşımlı hale geldiğinden metin görelidir.

1. Yeni **Project** iletişim kutusunda **Visual C#** veya  Visual Basic'ı genişletin ve ardından **Genişletilebilirlik'e tıklayın.** Şablonlar **bölmesinde** **VSIX'i seçin ve Project.** **Ad** kutusuna `TestAdornment` yazın. **Tamam**'a tıklayın.

2. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Visual C# **Genişletilebilirlik düğümüne gidin ve** Düzenleyici Metin **Donatma'ya gidin.** Varsayılan dosya adını *(Textİşlev1.cs/vb) bırakın.*

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *TextDornment1.cs* sınıfı `TextAdornment1` içerir.

    - *TextCreanment1TextViewCreationListener.cs* sınıfı `TextAdornment1TextViewCreationListener` içerir.

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür. Bir metin dosyası açarsanız, metindeki tüm 'a' karakterleri mavi arka plana karşı kırmızı olarak ana hatlarıyla özetler.

## <a name="create-a-viewport-relative-adornment-extension"></a>Görünüm görünümü göreli donatma uzantısı oluşturma
 Düzenleyici Görünüm Kutusu Donatma şablonu, görünüm kutusunun sağ üst köşesine kırmızı ana hatlı bir kutu ekleyen görünüm kutusu göreli bir donatma oluşturur.

> [!NOTE]
> Görünüm **kutusu,** şu anda görüntülenen metin görünümünün alanıdır.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Düzenleyici Görünüm Görünümü Donatma şablonunu kullanarak bir görünüm görünümü donatma uzantısı oluşturmak için

1. Yeni **Project** iletişim kutusunda **Visual C#** veya  Visual Basic'ı genişletin ve ardından **Genişletilebilirlik'e tıklayın.** Şablonlar **bölmesinde** **VSIX'i seçin ve Project.** **Ad** kutusuna `ViewportAdornment` yazın. **Tamam**'a tıklayın.

2. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Visual C# **Genişletilebilirlik düğümüne gidin ve** Düzenleyici GörünümPort **Donatım'ı seçin.** Varsayılan dosya adını *(Viewportİşlement1.cs/vb) bırakın.*

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *ViewportDornment1.cs* sınıfı `ViewportAdornment1` içerir.

    - *ViewportCreanment1TextViewCreationListener.cs* sınıfı `ViewportAdornment1TextViewCreationListener` içerir

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür. Yeni bir metin dosyası sanız, görünüm kutusunun sağ üst köşesinde kırmızı ana hatlı bir kutu görüntülenir.

## <a name="create-a-margin-extension"></a>Kenar boşluğu uzantısı oluşturma
 Düzenleyici Kenar Boşluğu şablonu* Merhaba dünya! sözcükleriyle birlikte görünen yeşil bir *kenar boşluğu oluşturur.* yatay kaydırma çubuğunun altında.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Düzenleyici Kenar Boşluğu şablonunu kullanarak bir kenar boşluğu uzantısı oluşturmak için

1. Yeni **Project** iletişim kutusunda **Visual C#** veya  Visual Basic'ı genişletin ve ardından **Genişletilebilirlik'e tıklayın.** Şablonlar **bölmesinde** **VSIX'i seçin ve Project.** **Ad** kutusuna `MarginExtension` yazın. **Tamam**'a tıklayın.

2. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Visual C# **Genişletilebilirlik düğümüne gidin ve Düzenleyici** Kenar **Boşluğu'nda öğesini seçin.** Varsayılan dosya adını (EditorMargin1.cs/vb) bırakın.

3. Aşağıdaki gibi iki kod dosyası vardır:

    - *EditorMargin1.cs* sınıfı `EditorMargin1` içerir.

    - *EditorMargin1Factory.cs* sınıfı `EditorMargin1Factory` içerir.

4. Bu projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür. Bir metin dosyası açarsanız, yatay kaydırma çubuğunun altında **Hello EditorMargin1** sözcüklerinin yer alan yeşil bir kenar boşluğu görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)

---
title: 'adım adım kılavuz: Metin Görünümü | Microsoft Docs'
description: Bu kılavuzda, düzenleyici biçimli haritasında yer alan çeşitli özelliklerden herhangi birini değiştirerek metin görünümünü özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fd60c6e9c6253a214de7a08173462895cdf29fc1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078550"
---
# <a name="walkthrough-customize-the-text-view"></a>Adım adım kılavuz: Metin görünümünü özelleştirme
Düzenleyici biçim haritasında aşağıdaki özelliklerden herhangi birini değiştirerek bir metin görünümünü özelleştirebilirsiniz:

- Gösterge kenar boşluğu

- Ekleme giriş karakteri

- Giriş imtiyazı üzerine yazma

- Seçili metin

- Etkin olmayan seçili metin (yani odağı kaybedilmiş seçili metin)

- Görünür boşluk

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>MEF projesi oluşturma

1. C# VSIX projesi oluşturun. (Yeni **Project** iletişim kutusunda Visual **C# / Genişletilebilirlik'i** seçin, ardından **VSIX Project**.) Çözüme adını `ViewPropertyTest` girin.

2. Projeye bir Düzenleyici Sınıflandırıcı öğesi şablonu ekleyin. Daha fazla bilgi için [bkz. Düzenleyici öğesi şablonuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Mevcut sınıf dosyalarını silin.

## <a name="define-the-content-type"></a>İçerik türünü tanımlama

1. Bir sınıf dosyası ekleyin ve olarak ad `ViewPropertyModifier` girin.

2. Aşağıdaki yönergeleri `using` ekleyin:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. 'den devralan `TestViewCreationListener` adlı bir sınıf bildir. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Bu sınıfı aşağıdaki özniteliklerle dışarı aktarın:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> bu dinleyicinin uygulanacağı içerik türünü belirtmek için.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> bu dinleyicinin rolünü belirtmek için.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. Bu sınıfta, içeri <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> aktarın.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Görünüm özelliklerini değiştirme

1. Görünüm açıldığında <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> görünüm özelliklerinin değişmesi için yöntemini ayarlayın. Değişikliği yapmak için, önce <xref:System.Windows.ResourceDictionary> bulmak istediğiniz görünümün yönüne karşılık gelen 'i bulun. Ardından kaynak sözlüğünde uygun özelliği değiştirin ve özellikleri ayarlayın. Özellikleri ayarlamadan önce yöntemini çağırarak yöntemine yapılan çağrıları toplu iş olarak ayarlayın ve ardından <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> özellikleri <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> ayardan sonra ' ı seçin.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Kodu derleme ve test

1. Çözümü derleyin.

     Bu projeyi hata ayıklayıcısında çalıştırarak, hata ayıklayıcısının Visual Studio örneği başlatıldı.

2. Bir metin dosyası oluşturun ve metin yazın.

    - Ekleme giriş karakteri magenta, üzerine yazma karakteri ise turququ.

    - Gösterge kenar boşluğu (metin görünümünün sol tarafından) açık yeşil renkli olması gerekir.

3. Yazdığınız metni seçin. Seçilen metnin rengi açık pembe olmalı.

4. Metin seçiliyken metin penceresinin dışındaki herhangi bir yere tıklayın. Seçilen metnin rengi koyu pembe olmalı.

5. Görünür boşluğu açma. (Düzenle menüsünde **Gelişmiş'in** üzerine **gelin ve ardından** Boşluğu **Görüntüle'ye tıklayın).** Metne bazı sekmeler yazın. Sekmeleri temsil eden kırmızı oklar görüntüleniyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Dil hizmeti ve düzenleyici uzantısı noktaları](../extensibility/language-service-and-editor-extension-points.md)

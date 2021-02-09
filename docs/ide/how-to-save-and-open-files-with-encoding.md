---
title: 'Nasıl yapılır: kodlama ile dosyaları kaydetme ve açma'
description: Belirli bir kodlamaya sahip dosyaları kaydetme ve açma hakkında bilgi edinin. dosyayı açtığınızda, Visual Studio dosyayı doğru şekilde görüntüler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d19b6f8e2e614ed397dee2e75807ded895a82d81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927918"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl yapılır: kodlama ile dosyaları kaydetme ve açma

Çift yönlü dilleri desteklemek için belirli karakter kodlamasına sahip dosyaları kaydedebilirsiniz. Ayrıca, dosyayı açarken bir kodlama belirtebilirsiniz, böylece Visual Studio dosyayı doğru şekilde görüntüler.

## <a name="to-save-a-file-with-encoding"></a>Kodlamalı bir dosyayı kaydetmek için

1. **Dosya** menüsünde **dosyayı farklı kaydet**' i seçin ve ardından **Kaydet** düğmesinin yanındaki açılan düğmeye tıklayın.

     **Gelişmiş kaydetme seçenekleri** iletişim kutusu görüntülenir.

2. **Kodlama** bölümünde dosya için kullanılacak kodlamayı seçin.

3. İsteğe bağlı olarak **satır sonları** altında satır sonu karakterlerinin biçimini seçin.

     Bu seçenek, dosyayı farklı bir işletim sistemi kullanıcılarıyla değiş tokuş etmek istiyorsanız yararlıdır.

     Belirli bir şekilde kodlandığını bildiğiniz bir dosyayla çalışmak istiyorsanız, Visual Studio 'Yu dosyayı açarken bu kodlamayı kullanmasını söyleyebilirsiniz. Kullandığınız yöntem, dosyanın projenizin bir parçası olup olmamasına bağlıdır.

> [!NOTE]
> Proje dosyasını kodlamalı olarak kaydetmek istiyorsanız, projeyi kaldırana kadar **dosyayı farklı kaydet** seçeneği etkinleştirilmez.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Projenin bir parçası olan kodlanmış bir dosyayı açmak için

1. **Çözüm Gezgini**, dosyaya sağ tıklayın ve **birlikte Aç**' ı seçin.

2. **Birlikte Aç** iletişim kutusunda dosyayı ile açmak için düzenleyiciyi seçin.

     Form Düzenleyicisi gibi birçok Visual Studio Düzenleyicisi, kodlamayı otomatik olarak algılayacak ve dosyayı uygun şekilde açacak. Bir kodlama seçmenize izin veren bir düzenleyici seçerseniz, **kodlama** iletişim kutusu görüntülenir.

3. **Kodlama** iletişim kutusunda düzenleyicinin kullanması gereken kodlamayı seçin.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Bir projenin parçası olmayan kodlanmış bir dosyayı açmak için

1. **Dosya** menüsünde **Aç**' ın üzerine gelin, Web 'den **Dosya** veya **Dosya**' yı seçin ve ardından açılacak dosyayı seçin.

2. **Aç** düğmesinin yanındaki açılan düğmeye tıklayın ve **birlikte Aç**' ı seçin.

3. Yukarıdaki yordamda 2. ve 3. adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlama ve satır sonları](encodings-and-line-breaks.md)
- [Kodlama ve Windows Forms Genelleştirme](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Uygulamaları globalize ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)

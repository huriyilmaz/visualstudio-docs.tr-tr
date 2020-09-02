---
title: 'Nasıl yapılır: kodlamaya sahip dosyaları kaydetme ve açma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9285a72137e4c2f3bdf54ef9f6535dedaa2cd5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670773"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl Yapılır: Dosyaları Kodlamayla Kaydetme ve Açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İki yönlü dilleri desteklemek için belirli karakter kodlamasına sahip dosyaları kaydedebilirsiniz. Ayrıca, dosyayı açarken bir kodlama belirtebilirsiniz, böylece Visual Studio dosyayı doğru şekilde görüntüler.

### <a name="to-save-a-file-with-encoding"></a>Kodlamalı bir dosyayı kaydetmek için

1. **Dosya** menüsünde **dosyayı farklı kaydet**' i seçin ve ardından **Kaydet** düğmesinin yanındaki açılan düğmeye tıklayın.

     **Gelişmiş kaydetme seçenekleri** iletişim kutusu görüntülenir.

2. **Kodlama**bölümünde dosya için kullanılacak kodlamayı seçin.

3. İsteğe bağlı olarak **satır sonları**altında satır sonu karakterlerinin biçimini seçin.

     Bu seçenek, dosyayı farklı bir işletim sistemi kullanıcılarıyla değiş tokuş etmek istiyorsanız yararlıdır.

     Belirli bir şekilde kodlandığını bildiğiniz bir dosyayla çalışmak istiyorsanız, Visual Studio 'Yu dosyayı açarken bu kodlamayı kullanmasını söyleyebilirsiniz. Kullandığınız yöntem, dosyanın projenizin bir parçası olup olmamasına bağlıdır.

### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Projenin bir parçası olan kodlanmış bir dosyayı açmak için

1. **Çözüm Gezgini**, dosyaya sağ tıklayın ve **birlikte Aç**' ı seçin.

2. **Birlikte Aç** iletişim kutusunda dosyayı ile açmak için düzenleyiciyi seçin.

     Form Düzenleyicisi gibi birçok Visual Studio Düzenleyicisi, kodlamayı otomatik olarak algılayacak ve dosyayı uygun şekilde açacak. Bir kodlama seçmenize izin veren bir düzenleyici seçerseniz, **kodlama** iletişim kutusu görüntülenir.

3. **Kodlama** iletişim kutusunda düzenleyicinin kullanması gereken kodlamayı seçin.

### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Bir projenin parçası olmayan kodlanmış bir dosyayı açmak için

1. **Dosya** menüsünde **Aç**' ın üzerine gelin, Web 'den **Dosya** veya **Dosya**' yı seçin ve ardından açılacak dosyayı seçin.

2. **Aç** düğmesinin yanındaki açılan düğmeye tıklayın ve **birlikte Aç**' ı seçin.

3. Yukarıdaki yordamda 2. ve 3. adımları izleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 Uygulama [Genelleştirme ve Windows Forms Genelleştirme](https://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9) [ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)

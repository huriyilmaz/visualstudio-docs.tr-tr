---
title: 'Nasıl yapılsın: Kodlama ile dosyaları kaydet ve aç'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1e562771567a6ff4f9dc35c9e98ceb5441a074
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596183"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl yapılsın: Kodlama ile dosyaları kaydet ve aç

Çift yönlü dilleri desteklemek için belirli karakter kodlaması içeren dosyaları kaydedebilirsiniz. Ayrıca, Visual Studio'nun dosyayı doğru şekilde görüntülemesi için dosyayı açarken bir kodlama da belirtebilirsiniz.

## <a name="to-save-a-file-with-encoding"></a>Kodlama ile bir dosyayı kaydetmek için

1. **Dosya** menüsünden **Dosyayı Farklı Kaydet'i**seçin ve ardından **Kaydet** düğmesinin yanındaki açılır düğmeyi tıklatın.

     **Gelişmiş Kaydet Seçenekleri** iletişim kutusu görüntülenir.

2. **Kodlama**altında, dosya için kullanılacak kodlamayı seçin.

3. İsteğe bağlı olarak, **Satır uçlarıaltında,** satır sonu karakterleri için biçimi seçin.

     Bu seçenek, dosyayı farklı bir işletim sisteminin kullanıcılarıyla değiştirmek istiyorsanız yararlıdır.

     Belirli bir şekilde kodlanmış olduğunu bildiğiniz bir dosyayla çalışmak istiyorsanız, Visual Studio'ya dosyayı açarken bu kodlamayı kullanmasını söyleyebilirsiniz. Kullandığınız yöntem, dosyanın projenizin bir parçası olup olmadığına bağlıdır.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Projenin parçası olan kodlanmış bir dosyayı açmak için

1. **Çözüm Gezgini'nde**, dosyayı sağ tıklatın ve **ile aç'ı**seçin.

2. Ile **Aç** iletişim kutusunda, dosyayı açmak için düzenleyiciyi seçin.

     Formlar düzenleyicisi gibi birçok Visual Studio düzenleyicisi, kodlamayı otomatik olarak algılar ve dosyayı uygun şekilde açar. Kodlama seçmenize olanak tanıyan bir düzenleyici seçerseniz, **Kodlama** iletişim kutusu görüntülenir.

3. **Kodlama** iletişim kutusunda, düzenleyicinin kullanması gereken kodlamayı seçin.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Projenin parçası olmayan kodlanmış bir dosyayı açmak için

1. **Dosya** menüsünde **Aç'ı**işaret edin, **Web'den** **Dosya** veya Dosya'yı seçin ve ardından açmak için dosyayı seçin.

2. **Aç** düğmesinin yanındaki açılır düğmeyi tıklatın ve **Ile Aç'ı**seçin.

3. Önceki yordamdan 2 ve 3 adımlarını izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlama ve satır sonları](encodings-and-line-breaks.md)
- [Kodlama ve Windows Formlar küreselleşme](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Uygulamaları küreselleştirin ve yerelleştirin](../ide/globalizing-and-localizing-applications.md)

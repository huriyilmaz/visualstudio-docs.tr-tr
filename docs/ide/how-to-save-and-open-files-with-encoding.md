---
title: 'Nasıl kullanılır: Dosyaları kodlamayla kaydetme ve açma'
description: Belirli bir kodlamayla dosyaları kaydetmeyi ve açmayı öğrenin. Bu nedenle, dosyayı Visual Studio doğru görüntülemeyi öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a3769689f28f1a14c39942c6cdcb0103e01bb8a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137385"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Nasıl kullanılır: Dosyaları kodlamayla kaydetme ve açma

Çift yönlü dilleri desteklemek için belirli karakter kodlamalı dosyaları kaydedebilirsiniz. Ayrıca, dosyayı doğru şekilde görüntülemesi için bir Visual Studio de belirtebilirsiniz.

## <a name="to-save-a-file-with-encoding"></a>Bir dosyayı kodlama ile kaydetmek için

1. Dosya **menüsünden** Dosyayı **Farklı Kaydet'i** seçin ve ardından Kaydet düğmesinin yanındaki açılan **düğmeye** tıklayın.

     Gelişmiş **Kaydetme Seçenekleri** iletişim kutusu görüntülenir.

2. Kodlama **altında,** dosya için kullanılacak kodlamayı seçin.

3. İsteğe bağlı **olarak, Satır sonu'nın** altında satır sonu karakterlerinin biçimini seçin.

     Bu seçenek, dosyayı farklı bir işletim sisteminin kullanıcıları ile değiştirme amacınız varsa kullanışlıdır.

     Belirli bir şekilde kodlanmış olduğunu bilirsiniz bir dosyayla çalışmak için, Visual Studio bu kodlamayı kullanmalarını sebilirsiniz. Kullandığınız yöntem, dosyanın projenizin bir parçası olup olmadığını bağlıdır.

> [!NOTE]
> Proje dosyasını kodlamayla kaydetmek için, **projeyi** kaldırana kadar Dosyayı Farklı Kaydet seçeneği etkinleştirilmez.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Projenin parçası olan kodlanmış bir dosyayı açmak için

1. Bu **Çözüm Gezgini** dosyasına sağ tıklayın ve Birlikte **Aç'ı seçin.**

2. Birlikte **Aç iletişim** kutusunda, dosyayı açmak için düzenleyiciyi seçin.

     Form Visual Studio gibi birçok farklı düzenleyici, kodlamayı otomatik olarak algılar ve dosyayı uygun şekilde açar. Kodlama seçmenize olanak sağlayan bir düzenleyici seçerseniz Kodlama **iletişim** kutusu görüntülenir.

3. Kodlama **iletişim** kutusunda düzenleyicinin kullanması gereken kodlamayı seçin.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Projenin parçası olan kodlanmış bir dosyayı açmak için

1. Dosya menüsünde **Aç'ın** üzerine **gelin,** Dosya **veya Web'den** **Dosya'ya** tıklayın ve ardından açılacak dosyayı seçin.

2. Aç düğmesinin yanındaki açılan düğmeye tıklayın **ve Birlikte** Aç'ı **seçin.**

3. Önceki yordamda yer alan 2. ve 3. Adımları izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodlama ve satır sonları](encodings-and-line-breaks.md)
- [Kodlama ve Windows Forms genelleştirmesi](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Uygulamaları genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)

---
title: 'Öğretici 2: Zamanlı matematik testi oluşturma'
description: Test sınavını alanların belirtilen süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test derlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 34518774d1580915911a502e4608d1b6e9bb879e
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517389"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Öğretici 2: Zamanlı matematik testi oluşturma

Bu öğreticide, test sınavını alan kişi belirli bir süre içinde dört rastgele aritmetik sorunu yanıtlaması gereken bir test oluşturacak.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic, bu nedenle kullanmakta olan programlama diline özgü bilgilere odaklanın.

Bu öğretici, aşağıdaki görevlerde size yol gösterir:

- sınıfını kullanarak rastgele sayılar <xref:System.Random> oluşturma.

- Bir denetim kullanarak olayları belirli bir zamanda gerçekleşmesini <xref:System.Windows.Forms.Timer> tetikler.

- Deyimleri kullanarak program `if else` akışını denetleme.

- Kodda temel aritmetik işlemler gerçekleştirme.

Bitirişte testiniz farklı sayılar dışında aşağıdaki ekran görüntüsüne benzer şekilde görünüyor:

![Dört sorunu olan matematik testi](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Öğretici bağlantıları

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Proje oluşturma ve formunuza etiketler ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Başlangıç olarak projeyi oluşturma, özellikleri değiştirme ve denetimler `Label` ekleme.|
|[2. Adım: Rastgele bir toplama problemi oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Bir toplama sorunu oluşturun ve rastgele sayılar `Random` oluşturmak için sınıfını kullanın.|
|[3. Adım: Geri sayım zamanlayıcısı ekleme](../ide/step-3-add-a-countdown-timer.md)|Testin zamanlayıcısı için bir geri sayım zamanlayıcısı ekleyin.|
|[4. Adım: CheckTheAnswer() yöntemi ekleme](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınava girenin sorun için doğru yanıtı içerip gire olmadığını kontrol etmek için bir yöntem ekleyin.|
|[5. Adım: NumericUpDown denetimleri için Giriş olay işleyicileri ekleme](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Testlerinizi kolaylaştıran olay işleyicileri ekleyin.|
|[6. Adım: Çıkarma problemi ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rastgele sayılar oluşturan, zamanlayıcıyı kullanan ve doğru yanıtları kontrol etmeyen bir çıkarma problemi ekleyin.|
|[7. Adım: Çarpma ve bölme problemleri ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rastgele sayılar oluşturan çarpma ve bölme sorunları ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[8. Adım: Testi özelleştirme](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için **[1. Adım: Proje oluşturun ve formnize etiketler ekleyin.](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# öğreticileri](../get-started/csharp/index.yml)
* [Visual Basic öğreticileri](../get-started/visual-basic/index.yml)
* [C++ öğreticileri](/cpp/get-started/tutorial-console-cpp)
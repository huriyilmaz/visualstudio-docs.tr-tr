---
title: 'Öğretici 2: Zamanlanmış matematik testi oluşturma'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b1f3620ef462228ff6a3461f44019e9c515a1c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579310"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Öğretici 2: Zamanlanmış matematik testi oluşturma

Bu eğitimde, sınav katılımcısının belirli bir süre içinde dört rasgele aritmetik sorunu yanıtlaması gereken bir test oluşturursunuz.

> [!NOTE]
> Bu öğretici hem C# hem de Visual Basic'i kapsar, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.

Bu öğretici aşağıdaki görevleri size yol sağlar:

- <xref:System.Random> Sınıfı kullanarak rasgele sayılar oluşturun.

- Denetim <xref:System.Windows.Forms.Timer> kullanarak belirli bir zamanda oluşacak olayları tetikler.

- İfadeleri kullanarak `if else` program akışını kontrol edin.

- Temel aritmetik işlemleri kod halinde gerçekleştirin.

Bitirdiğinizde, sınavınız farklı numaralar dışında aşağıdaki ekran görüntüsüne benzer:

![Dört problemli matematik testi](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Öğretici bağlantılar

|Başlık|Açıklama|
|-----------|-----------------|
|[Adım 1: Proje oluşturma ve forma etiket ekleme](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Projeyi oluşturarak, özellikleri değiştirerek `Label` ve denetimler ekleyerek başlayın.|
|[Adım 2: Rasgele ekleme sorunu oluşturma](../ide/step-2-create-a-random-addition-problem.md)|Bir ek sorun oluşturun `Random` ve rasgele sayılar oluşturmak için sınıfı kullanın.|
|[Adım 3: Geri sayım sayıcı ekleme](../ide/step-3-add-a-countdown-timer.md)|Testin zamanlanabilmesi için geri sayım sayıcıekleyin.|
|[Adım 4: CheckTheAnswer() yöntemini ekleyin](../ide/step-4-add-the-checktheanswer-parens-method.md)|Sınav alıyanıtının sorun için doğru yanıtı girip girmediğini kontrol etmek için bir yöntem ekleyin.|
|[Adım 5: SayısalUpDown denetimleri için olay işleyicileri girin](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Testinizi daha kolay yapan etkinlik işleyicileri ekleyin.|
|[Adım 6: Çıkarma sorunu ekleme](../ide/step-6-add-a-subtraction-problem.md)|Rasgele sayılar üreten, zamanlayıcıyı kullanan ve doğru yanıtları denetleyen bir çıkarma sorunu ekleyin.|
|[Adım 7: Çarpma ve bölme problemleri ekleme](../ide/step-7-add-multiplication-and-division-problems.md)|Rasgele sayılar oluşturan çarpma ve bölme sorunlarını ekleyin, zamanlayıcıyı kullanın ve doğru yanıtları denetleyin.|
|[Adım 8: Testi özelleştirin](../ide/step-8-customize-the-quiz.md)|Renkleri değiştirme ve ipucu ekleme gibi diğer özellikleri deneyin.|

Ayrıca büyük, ücretsiz video öğrenme kaynakları sizin için kullanılabilir. C#'da programlama hakkında daha fazla bilgi edinmek [için C# temellerine bakın: Yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Visual Basic'te programlama hakkında daha fazla bilgi edinmek [için Visual Basic temellerine bakın: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiye başlamak için Adım 1 ile **[başlayın: Bir proje oluşturun ve formunuza etiket ekleyin.](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**

## <a name="see-also"></a>Ayrıca bkz.

* [Diğer C# eğitimleri](/visualstudio/get-started/csharp/)
* [Visual Basic eğitimleri](/visualstudio/get-started/visual-basic/)
* [C++ eğitimleri](/cpp/get-started/tutorial-console-cpp)

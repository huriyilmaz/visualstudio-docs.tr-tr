---
title: R kodu için IntelliSense
description: Visual Studio IntelliSense, R kodu yazarken işlevler, nesne üyeleri, kod parçacıkları ve tamamlamalar hakkındaki bilgileri görüntüler.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: de6a8ffbaa0fb10929d013a351ebffa8e3f4b529
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939441"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense, kod yazarken doğrudan görünüminizdeki nesne, işlev bağımsız değişkenleri ve [kod parçacıkları](code-snippets-for-r.md) hakkında çağırabilmeniz için kullanabileceğiniz işlevlerle ilgili bilgileri görüntüler. Ayrıca, yazarken olası tamamlanmalar görüntülenir ve **sekmeye** bastığınızda veya tuşları **girerken** tamamlanır ( **Gelişmiş** sekmesi için [Düzenleyici seçeneklerine](editing-r-code-in-visual-studio.md#editor-options) bakın). IntelliSense hem düzenleyicide hem de [etkileşimli pencerede](interactive-repl-for-r-in-visual-studio.md)kullanılabilir.

![İşlev imzasını gösteren IntelliSense](media/intellisense-function-signature.png)

Bir işlev veya başka bir ifade yazarken, IntelliSense zaten girdiklerinize göre filtrelenmiş bir otomatik tamamlama menüsü (case-sensitively) sağlar:

![IntelliSense otomatik tamamlama menüsü](media/intellisense-auto-complete-menu.png)

**Sekmeye** basmak (veya seçeneklerin nasıl ayarlandığına bağlı olarak **ENTER** veya **boşluk**), açılan menüde seçilen öğeyi ekler. Seçimi ok tuşlarıyla değiştirebilirsiniz.

IntelliSense, R nesnelerinin üyeleri için de öneriler sağlar:

![Nesne üyeleri için IntelliSense önerileri](media/intellisense-auto-complete-r-objects.png)

**ESC** tuşuna basmak menüyü tamamen geri atar. **CTRL** Space 'i kullanarak geri dönebilirsiniz + .

`(`Bir işlev çağrısının açılmasını yazmak, kapatmayı ekler `)` ve daha önce gösterildiği gibi imza yardımını getirir:

![Bir işlev için IntelliSense imza yardımı](media/intellisense-function-signature.png)

Daha sonra **ESC** , açılan pencereyi kapatır; işlev imzaları için, **CTRL** + **vardiyası** + **alanı** ile tekrar getirebilirsiniz.

> [!Tip]
> Parametresi altındaki metni gizler hale getirmek için **CTRL** tuşuna basılı tutarak parametre yardım metnini yarı saydam yapın.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Kullanıcı tanımlı işlevler ve değişkenler için IntelliSense

IntelliSense, ad parametresi tamamlama da dahil olmak üzere, aynı dosyadaki Kullanıcı tanımlı işlevler için geçerlidir:

![Kullanıcı tanımlı işlevler için IntelliSense](media/intellisense-same-file-functions.png)

![Kullanıcı tanımlı işlevler için IntelliSense parametre tamamlama](media/intellisense-parameter-completion.png)

IntelliSense aynı dosyadaki ve geçerli oturumdaki değişkenler için de geçerlidir:

![IntelliSense değişken tamamlama](media/intellisense-variable-completion.png)

> [!Note]
> Etkileşimli pencerede, IntelliSense yalnızca geçerli R oturumunda adları kabul eder ve projenizdeki dosyaları yoksayar.

## <a name="code-suggestions"></a>Kod önerileri

Kenar boşluğunda bir ampul (akıllı etiket olarak adlandırılır) göründüğünde, Visual Studio yaygın olarak kullanılan bir eylem için kullanılabilen bir kısayol olduğunu önerir. Örneğin, `library` bir ampul görmek için düzenleyicide bir ifade içeren bir çizginin üzerine gelin. Ampul seçildiğinde kullanılabilen seçenekler görüntülenir:

![Düzenleyicide R için Akıllı Etiketler](media/intellisense-smart-tags.png)

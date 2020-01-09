---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: Ifade düzenleyicisini kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff5654214809cf2f57767005153ba557df487c1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584549"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl yapılır: Ifade düzenleyicisini kullanma

Ifade Düzenleyicisi, ifadeleri girmek ve değerlendirmek için birçok iş akışı aktivitelerinde kullanılan bir İş Akışı Tasarımcısı denetimidir. Ifade Düzenleyicisi, diğer özelliklerin yanı sıra IntelliSense, renklendirme, ParamInfo, Error dalgalı çizgiler dahil olmak üzere tam kapsamlı bir IDE düzenleme deneyimi sağlar. Derleyici, ifadeyi girdikten sonra doğrular. İfade geçersizse, bir hata simgesi görüntülenir. Düzenleyici Ayrıca bir **Ifade Düzenleyicisi** iletişim kutusu olarak açılabilir.

İfadeler değişmez değerlerdir veya bağımsız değişkenlere veya özelliklere göre Visual Basic kodudur. Bunlar, yeni bir değer sağlamak için işlemlerle birleştirilmiş değer öğeleri (örneğin, değişkenler, sabitler, sabit değerler, Özellikler) içerirler. Uygulamalar, kullanan C#bir programda olsa bile vb.NET sözdizimi kullanılarak yazılır. Bu, büyük/küçük harf, tek bir eşittir işareti ("=" yerine "=") kullanılarak gerçekleştirilmiş olması anlamına gelir, Boole işleçleri "& &" ve "| |" sembolleri yerine "and" ve "veya" kelimeleridir ve **null**yerine **hiçbir şey** kullanılmaz. Visual Basic ifade ve işleçler hakkında daha fazla bilgi için ve bazı örnekler için bkz. [Visual Basic işleçler ve ifadeler](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Ifade Düzenleyicisi** aşağıdaki gibi davranır:

- Odak, Ifade düzenleyicide yoksa, normal bir TextBlock denetimi gibi görünür.

- Odak, Ifade düzenleyiciden olduktan sonra Ifade Düzenleyicisi denetimi gibi görünür ve davranır. Odak kesildiğinde, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

- Yeniden barındırılan bir iş akışı tasarımcısında Ifade düzenleyicisine odaklanıyorsanız, bir metin kutusu gibi davranır. Yeniden barındırılan iş akışı tasarımcısında odak kaybedildiği zaman, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

> [!NOTE]
> Ifade Düzenleyicisi için IntelliSense yalnızca Visual Studio içinde kullanılabilir. Hem Visual Studio 'da hem de yeniden barındırılan senaryolarda, derleyici girildikten sonra ifadeyi doğrular ve ifade geçersizse ifade Düzenleyicisi bir hata simgesi görüntüler.

## <a name="use-the-expression-editor"></a>İfade Düzenleyicisini Kullanma

1. Visual Studio 'da yeni veya var olan bir iş akışı projesi açın.

2. İş akışınıza <xref:System.Activities.Statements.Assign> etkinliği ekleyin.

    > [!NOTE]
    > Birden çok iş akışı etkinliği ifade düzenleyicilerine sahiptir. İfade TextBlocks, değişken tasarımcısında, bağımsız değişken tasarımcısında ve dinamik bağımsız değişken tasarımcısında de görünür. <xref:System.Activities.Statements.Assign> etkinliği örnek olarak kullanılır.

3. <xref:System.Activities.Statements.Assign> etkinliği için Etkinlik tasarımcısında sol ifade düzenleyicisine tıklayın.

     Gri filigran dizeleri **\<** ve **\<bir VB ifadesi girer >** <xref:System.Activities.Statements.Assign> etkinliğinde ifade düzenleyicileri için varsayılan metin dizeleridir.

4. Deyiminizi girin. Bir dize girerseniz, dizenin etrafına tırnak işareti yerleştirdiğinizden emin olun. İfade bağımsız değişkenini bir değişkene bağlamayı seçerseniz, tırnak işaretlerini kapalı bırakın.

     İşiniz bittiğinde, odağı tasarımcının başka bir bölümüne kaydırmak için Ifade Düzenleyicisi dışında bir bölge veya alan seçin. Odak kaydırma, derleyicinin ifadeyi daha önce açıklandığı gibi doğrulamasına neden olur.

     Bir ifadeyi girmeye veya düzenlemeye yönelik alternatif bir yöntem, özellik kılavuzundaki Özellik adının yanındaki üç nokta simgesine tıklayadır. Üç nokta seçildiğinde, **Ifade Düzenleyicisi** bir iletişim kutusu olarak açılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>

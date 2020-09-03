---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: Ifade düzenleyicisini kullanma'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04c0fdaab87c88028b8c14ca59e93fa93e74be74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817443"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl Yapılır: İfade Düzenleyicisini Kullanma

Ifade Düzenleyicisi, ifadeleri girmek ve değerlendirmek için birçok iş akışı aktivitelerinde kullanılan bir İş Akışı Tasarımcısı denetimidir. Ifade Düzenleyicisi, diğer özelliklerin yanı sıra IntelliSense, renklendirme, ParamInfo, Error dalgalı çizgiler dahil olmak üzere tam kapsamlı bir IDE düzenleme deneyimi sağlar. Derleyici, ifadeyi girdikten sonra doğrular. İfade geçersizse, bir hata simgesi görüntülenir. Düzenleyici Ayrıca bir **Ifade Düzenleyicisi** iletişim kutusu olarak açılabilir.

İfadeler değişmez değerlerdir veya bağımsız değişkenlere veya özelliklere göre Visual Basic kodudur. Bunlar, yeni bir değer sağlamak için işlemlerle birleştirilmiş değer öğeleri (örneğin, değişkenler, sabitler, sabit değerler, Özellikler) içerirler. Uygulamalar C# kullanan bir programda olsa bile, VB.NET sözdizimi kullanılarak ifadeler yazılır. Bu, büyük/küçük harf, tek bir eşittir işareti ("=" yerine "=") kullanılarak gerçekleştirilmiş olması anlamına gelir, Boole işleçleri "&&" ve "| |" sembolleri yerine "and" ve "veya" kelimeleridir ve **null**yerine **hiçbir şey** kullanılmaz. Visual Basic ifade ve işleçler hakkında daha fazla bilgi için ve bazı örnekler için bkz. [Visual Basic işleçler ve ifadeler](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Ifade Düzenleyicisi** aşağıdaki gibi davranır:

- Odak, Ifade düzenleyicide yoksa, normal bir TextBlock denetimi gibi görünür.

- Odak, Ifade düzenleyiciden olduktan sonra Ifade Düzenleyicisi denetimi gibi görünür ve davranır. Odak kesildiğinde, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

- Yeniden barındırılan bir iş akışı tasarımcısında Ifade düzenleyicisine odaklanıyorsanız, bir metin kutusu gibi davranır. Yeniden barındırılan iş akışı tasarımcısında odak kaybedildiği zaman, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

> [!NOTE]
> Ifade Düzenleyicisi için IntelliSense yalnızca Visual Studio içinde kullanılabilir. Hem Visual Studio 'da hem de yeniden barındırılan senaryolarda, derleyici girildikten sonra ifadeyi doğrular ve ifade geçersizse ifade Düzenleyicisi bir hata simgesi görüntüler.

## <a name="use-the-expression-editor"></a>İfade Düzenleyicisini Kullanma

1. Visual Studio 'da yeni veya var olan bir iş akışı projesi açın.

2. <xref:System.Activities.Statements.Assign>İş akışınıza etkinlik ekleyin.

    > [!NOTE]
    > Birden çok iş akışı etkinliği ifade düzenleyicilerine sahiptir. İfade TextBlocks, değişken tasarımcısında, bağımsız değişken tasarımcısında ve dinamik bağımsız değişken tasarımcısında de görünür. <xref:System.Activities.Statements.Assign>Etkinlik örnek olarak kullanılır.

3. Etkinlik için Etkinlik tasarımcısında sol ifade düzenleyicisine tıklayın <xref:System.Activities.Statements.Assign> .

     Gri filigran dizeleri **\<To>** ve **\<Enter a VB Expression>** etkinlik içindeki ifade düzenleyicileri için varsayılan metin dizeleridir <xref:System.Activities.Statements.Assign> .

4. Deyiminizi girin. Bir dize girerseniz, dizenin etrafına tırnak işareti yerleştirdiğinizden emin olun. İfade bağımsız değişkenini bir değişkene bağlamayı seçerseniz, tırnak işaretlerini kapalı bırakın.

     İşiniz bittiğinde, odağı tasarımcının başka bir bölümüne kaydırmak için Ifade Düzenleyicisi dışında bir bölge veya alan seçin. Odak kaydırma, derleyicinin ifadeyi daha önce açıklandığı gibi doğrulamasına neden olur.

     Bir ifadeyi girmeye veya düzenlemeye yönelik alternatif bir yöntem, özellik kılavuzundaki Özellik adının yanındaki üç nokta simgesine tıklayadır. Üç nokta seçildiğinde, **Ifade Düzenleyicisi** bir iletişim kutusu olarak açılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>

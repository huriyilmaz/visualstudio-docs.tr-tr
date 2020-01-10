---
title: 'Nasıl yapılır: Ifade düzenleyicisini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54099bc5c0f249cdb3697715d153a94a596ac344
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849228"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl yapılır: Ifade düzenleyicisini kullanma
Ifade Düzenleyicisi, bu ifadeleri girme ve değerlendirme yöntemi olarak birçok iş akışı aktivitelerinde kullanılan bir [!INCLUDE[wfd1](../includes/wfd1-md.md)] denetimidir. Ifade Düzenleyicisi, diğer özelliklerin yanı sıra IntelliSense, renklendirme, ParamInfo, Error dalgalı çizgiler dahil olmak üzere tam kapsamlı bir IDE düzenleme deneyimi sağlar. Derleyici, ifadeyi girdikten sonra doğrular. İfade geçersizse, bir hata simgesi görüntülenir. Düzenleyici Ayrıca bir **Ifade Düzenleyicisi** iletişim kutusu olarak açılabilir.

 İfadeler değişmez değerlerdir veya bağımsız değişkenlere veya özelliklere göre [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodudur. Yeni bir değer sağlamak için işlemlerle birleştirilmiş değer öğeleri (örn. değişkenler, sabitler, sabit değerler, Özellikler) içerirler. Uygulamalar, kullanan C#bir programda olsa bile vb.NET sözdizimi kullanılarak yazılır. Bu, büyük/küçük harf kullanımının ("= =") yerine tek bir eşittir ("=") işareti kullanılarak gerçekleştirildiğinden, Boole işleçleri "& &" ve "&#124;&#124;" sembolleri yerine "and" ve "or" kelimeleridir ve **null**yerine **hiçbir şey** kullanılmaz. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifade ve işleçler hakkında daha fazla bilgi için ve bazı örnekler için bkz. [Visual Basic işleçler ve ifadeler](https://msdn.microsoft.com/library/a1w3te48(VS.100).aspx).

 **Ifade Düzenleyicisi** aşağıdaki gibi davranır:

- Odak, Ifade düzenleyicide yoksa, normal bir TextBlock denetimi gibi görünür.

- Odak, Ifade düzenleyiciden olduktan sonra Ifade Düzenleyicisi denetimi gibi görünür ve davranır. Odağı kaybetduktan sonra, normal bir TextBlock gibi görünür.

- Yeniden barındırılan bir iş akışı tasarımcısında Ifade düzenleyicisine odaklanıyorsanız, bir metin kutusu gibi davranır. Yeniden barındırılan iş akışı tasarımcısında odak kaybedildiği zaman, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

> [!NOTE]
> Ifade Düzenleyicisi için IntelliSense yalnızca [!INCLUDE[vs2010](../includes/vs2010-md.md)]içinde kullanılabilir. Hem [!INCLUDE[vs2010](../includes/vs2010-md.md)] hem de yeniden barındırılan senaryolarda, derleyici girildikten sonra ifadeyi doğrular ve ifade geçersizse ifade Düzenleyicisi bir hata simgesi görüntüler.

### <a name="using-the-expression-editor"></a>Ifade düzenleyicisini kullanma

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]' de, yeni veya mevcut bir iş akışı projesi açın.

2. İş akışınıza <xref:System.Activities.Statements.Assign> etkinliği ekleyin.

    > [!NOTE]
    > Birden çok iş akışı etkinliği ifade düzenleyicilerine sahiptir. İfade TextBlocks, değişken tasarımcısında, bağımsız değişken tasarımcısında ve dinamik bağımsız değişken tasarımcısında de görünür. <xref:System.Activities.Statements.Assign> etkinliği örnek olarak kullanılır.

3. <xref:System.Activities.Statements.Assign> etkinliği için Etkinlik tasarımcısında sol ifade düzenleyicisine tıklayın.

     Gri eşik dizeleri **\<** ve **\<bir VB ifadesi girer >** <xref:System.Activities.Statements.Assign> etkinliğinde ifade düzenleyicilerinin varsayılan metin dizeleridir.

4. Deyiminizi girin. Bir dize girerseniz, dizenin etrafına tırnak işareti yerleştirdiğinizden emin olun. İfade bağımsız değişkenini bir değişkene bağlamayı seçerseniz, tırnak işaretlerini kapalı bırakın.

     İşiniz bittiğinde, odağı tasarımcının başka bir bölümüne kaydırmak için Ifade Düzenleyicisi dışında bir bölge veya alan seçin. Bu, derleyicinin ifadeyi daha önce açıklandığı gibi doğrulamasına neden olur.

     Bir ifadeyi girmeye veya düzenlemeye yönelik alternatif bir yöntem, özellik kılavuzundaki Özellik adının yanındaki üç nokta simgesine tıklayadır. Bu işlem, **Ifade Düzenleyicisi** iletişim kutusunu açar.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Activities.Presentation.View.ExpressionTextBox>

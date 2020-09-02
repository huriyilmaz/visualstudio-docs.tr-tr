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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849228"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl Yapılır: İfade Düzenleyicisini Kullanma
Ifade Düzenleyicisi, [!INCLUDE[wfd1](../includes/wfd1-md.md)] Bu ifadeleri girme ve değerlendirme yöntemi olarak birçok iş akışı aktivitelerinde kullanılan bir denetimdir. Ifade Düzenleyicisi, diğer özelliklerin yanı sıra IntelliSense, renklendirme, ParamInfo, Error dalgalı çizgiler dahil olmak üzere tam kapsamlı bir IDE düzenleme deneyimi sağlar. Derleyici, ifadeyi girdikten sonra doğrular. İfade geçersizse, bir hata simgesi görüntülenir. Düzenleyici Ayrıca bir **Ifade Düzenleyicisi** iletişim kutusu olarak açılabilir.

 İfadeler değişmez değerlerdir veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] bağımsız değişkenlere veya özelliklere bağlanır. Yeni bir değer sağlamak için işlemlerle birleştirilmiş değer öğeleri (örn. değişkenler, sabitler, sabit değerler, Özellikler) içerirler. Uygulamalar C# kullanan bir programda olsa bile, VB.NET sözdizimi kullanılarak ifadeler yazılır. Bu, büyük/küçük harf kullanımının ("= =") yerine tek bir eşittir ("=") işareti kullanılarak gerçekleştirildiğinden, Boole işleçleri "&&" ve "&#124;&#124;" sembolleri yerine "and" ve "or" kelimeleridir ve **null**yerine **hiçbir şey** kullanılmaz. İçindeki ifadeler ve işleçler hakkında daha fazla bilgi için [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve bazı örnekler için [Visual Basic içindeki Işleçler ve ifadeler](https://msdn.microsoft.com/library/a1w3te48(VS.100).aspx)bölümüne bakın.

 **Ifade Düzenleyicisi** aşağıdaki gibi davranır:

- Odak, Ifade düzenleyicide yoksa, normal bir TextBlock denetimi gibi görünür.

- Odak, Ifade düzenleyiciden olduktan sonra Ifade Düzenleyicisi denetimi gibi görünür ve davranır. Odağı kaybetduktan sonra, normal bir TextBlock gibi görünür.

- Yeniden barındırılan bir iş akışı tasarımcısında Ifade düzenleyicisine odaklanıyorsanız, bir metin kutusu gibi davranır. Yeniden barındırılan iş akışı tasarımcısında odak kaybedildiği zaman, Ifade Düzenleyicisi normal bir TextBlock gibi görünür.

> [!NOTE]
> Ifade Düzenleyicisi için IntelliSense yalnızca içinde kullanılabilir [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Hem hem de [!INCLUDE[vs2010](../includes/vs2010-md.md)] yeniden barındırılan senaryolarda, derleyici girildikten sonra ifadeyi doğrular ve ifade geçersizse ifade Düzenleyicisi bir hata simgesi görüntüler.

### <a name="using-the-expression-editor"></a>Ifade düzenleyicisini kullanma

1. İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)] , yeni veya var olan bir iş akışı projesi açın.

2. <xref:System.Activities.Statements.Assign>İş akışınıza etkinlik ekleyin.

    > [!NOTE]
    > Birden çok iş akışı etkinliği ifade düzenleyicilerine sahiptir. İfade TextBlocks, değişken tasarımcısında, bağımsız değişken tasarımcısında ve dinamik bağımsız değişken tasarımcısında de görünür. <xref:System.Activities.Statements.Assign>Etkinlik örnek olarak kullanılır.

3. Etkinlik için Etkinlik tasarımcısında sol ifade düzenleyicisine tıklayın <xref:System.Activities.Statements.Assign> .

     Gri filigran dizeleri **\<To>** ve **\<Enter a VB Expression>** etkinlik içindeki ifade düzenleyicileri için varsayılan metin dizeleridir <xref:System.Activities.Statements.Assign> .

4. Deyiminizi girin. Bir dize girerseniz, dizenin etrafına tırnak işareti yerleştirdiğinizden emin olun. İfade bağımsız değişkenini bir değişkene bağlamayı seçerseniz, tırnak işaretlerini kapalı bırakın.

     İşiniz bittiğinde, odağı tasarımcının başka bir bölümüne kaydırmak için Ifade Düzenleyicisi dışında bir bölge veya alan seçin. Bu, derleyicinin ifadeyi daha önce açıklandığı gibi doğrulamasına neden olur.

     Bir ifadeyi girmeye veya düzenlemeye yönelik alternatif bir yöntem, özellik kılavuzundaki Özellik adının yanındaki üç nokta simgesine tıklayadır. Bu işlem, **Ifade Düzenleyicisi** iletişim kutusunu açar.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Activities.Presentation.View.ExpressionTextBox>

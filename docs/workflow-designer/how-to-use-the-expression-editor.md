---
title: 'İş Akışı Tasarımcısı - Nasıl: İfade Düzenleyicisini Kullanma'
description: İfade Düzenleyicisi'nin ifadeleri girmek İş Akışı Tasarımcısı değerlendirmek için birçok iş akışı etkinlikte kullanabileceğiniz bir denetim denetimi olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 9cba7dfc832eca703991b110254a60edc3bae054
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963702"
---
# <a name="how-to-use-the-expression-editor"></a>Nasıl Yapılır: İfade Düzenleyicisini Kullanma

İfade Düzenleyicisi, ifadeleri İş Akışı Tasarımcısı değerlendirmek için birçok iş akışı etkinliklerinde kullanılan bir denetimdir. İfade Düzenleyicisi IntelliSense, renklendirme, ParamInfo, hata geçişleri ve diğer özellikler de dahil olmak üzere tam özelliklere sahip bir IDE düzenleme deneyimi sağlar. Derleyici, girdikten sonra ifadeyi doğrular. İfade geçersizse bir hata simgesi görüntülenir. Düzenleyici bir İfade Düzenleyicisi iletişim **kutusu olarak da** açılabilir.

İfadeler sabit değerlerdir veya Visual Basic veya özelliklere bağlı koddur. Yeni bir değer elde etmek için işlemlerle birleştirilmiş değer öğelerini (örneğin, değişkenler, sabitler, değişmez değerler, özellikler) içerirler. İfadeler, uygulama C# VB.NET bir programda olsa bile söz dizimi kullanılarak yazılır. Başka bir deyişle büyük harf kullanımı önemli değildir, karşılaştırma tek bir eşittir işareti ("==" yerine "=" kullanılarak), Boole işleçleri "&&" ve "||" simgeleri yerine "and" ve "or" sözcükleridir ve **Null** yerine **Nothing** kullanılır. Visual Basic ve bazı örneklerde ifade ve işleçler hakkında daha fazla bilgi için [bkz.](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))Visual Basic.

İfade **Düzenleyicisi** aşağıdaki gibi davranır:

- Odak İfade Düzenleyicisi'nde yoksa normal bir TextBlock denetimi gibi görünüyor.

- Odak İfade Düzenleyicisi'ne olduktan sonra İfade Düzenleyicisi denetimi gibi davranır ve davranır. Odak kaybedildikten sonra İfade Düzenleyicisi tekrar normal bir TextBlock gibi görünüyor.

- Yeniden barındırılan bir iş akışı tasarımcısında İfade Düzenleyicisi'ne odaklanırsanız, metin kutusu gibi davranır. Yeniden barındırılan iş akışı tasarımcısında odak kaybolursa, İfade Düzenleyicisi tekrar normal bir TextBlock gibi görünüyor.

> [!NOTE]
> İfade Düzenleyicisi için IntelliSense yalnızca Visual Studio. Hem Visual Studio yeniden barındırılan senaryolarda, derleyici girdikten sonra ifadeyi doğrular ve ifade geçersizse ifade düzenleyicisi bir hata simgesi görüntüler.

## <a name="use-the-expression-editor"></a>İfade Düzenleyicisini Kullanma

1. Bu Visual Studio yeni veya mevcut bir iş akışı projesi açın.

2. Örneğin, etkinliği iş <xref:System.Activities.Statements.Assign> akışınıza ekleyin.

    > [!NOTE]
    > Birden çok iş akışı etkinliklerinin ifade düzenleyicileri vardır. İfade Metin Engellemeleri değişken tasarımcısında, bağımsız değişken tasarımcısında ve dinamik bağımsız değişken tasarımcısında da görünür. Etkinlik <xref:System.Activities.Statements.Assign> örnek olarak kullanılır.

3. Etkinlik tasarımcısında etkinlik için sol ifade düzenleyicisine <xref:System.Activities.Statements.Assign> tıklayın.

     gri filigran dizeleri ve **\<To>** **\<Enter a VB Expression>** etkinlikte ifade düzenleyicileri için varsayılan metin <xref:System.Activities.Statements.Assign> dizeleridir.

4. İfadenizi girin. Bir dize girersiniz, dizenin etrafına tırnak işaretleri koyarak emin olun. İfade bağımsız değişkenlerini bir değişkene bağlamayı seçerseniz tırnak işaretlerini kapalı bırakın.

     Bitirerek Odağı tasarımcının başka bir parçasına kaydırmak için İfade Düzenleyicisi'nin dışında bir bölge veya alan seçin. Odağı kaydırmak, derleyicinin daha önce açıklandığı gibi ifadeyi doğrulamalarına neden olur.

     bir ifadeyi girmenin veya düzenlemenin alternatif bir yolu, özellik kılavuzunda özellik adının yanındaki üç nokta tıklamaktır. Üç noktanın seçimi, İfade **Düzenleyicisi'ni bir** iletişim kutusu olarak açar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.View.ExpressionTextBox>

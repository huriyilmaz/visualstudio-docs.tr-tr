---
title: Office çözümleri geliştirme
description: Visual Studio 'da Office geliştirici araçlarını kullanarak bir projeyi tasarlamayı öğrenin. Ayrıca, kodu ve özel kullanıcı arabirimini (UI) uygulamaya nasıl başlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fbfe569e587c53aede6d550bc20527ad8d0fd328
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845004"
---
# <a name="develop-office-solutions"></a>Office çözümleri geliştirme
  Visual Studio 'da Office geliştirici araçlarını kullanarak bir proje tasarladıktan ve proje dosyalarını ayarladıktan sonra, kodu ve özel kullanıcı arabirimini (UI) uygulamaya odaklanabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Office çözümleri programlama modeli
 Office nesne modeli, programlama yapacağımız çeşitli nesneler sunar. Yönetilen kod kullanarak Office çözümlerini programlayışınızda, Office birincil birlikte çalışma derlemelerindeki türler kullanan kodu yazarsınız. Visual Studio 'da Office proje şablonlarını kullanarak oluşturduğunuz çözümlerde, doğrudan projenizdeki oluşturulan sınıflara göre de kod yazarsınız. Daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Office çözümlerinin farklı türlerini programlama
 Oluşturmakta olduğunuz çözüm türü, projenizde hangi özellikleri kullanabileceğinizi belirler. Örneğin, tasarım zamanında Visual Studio 'daki **araç kutusundan** öğeleri sürükleyerek belge düzeyi özelleştirmelere Windows Forms denetimleri ve genişletilmiş Office denetimleri ( *konak denetimleri* olarak adlandırılır) ekleyebilirsiniz. Ancak, VSTO eklentisi geliştiriyorsanız, kod yazarak bu denetim türlerini yalnızca çalışma zamanında belgelere ekleyebilirsiniz.

 Farklı çözüm türlerine özgü özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

- [Program belge düzeyinde özelleştirmeler](../vsto/programming-document-level-customizations.md).

- [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

  Proje oluşturmanıza yardımcı olmak üzere Office çözümlerini ve yordamlarını planlamaya yardımcı olacak arka plan bilgileri için, bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)|Office çözümlerinde kod yazmanın farklı yönlerini açıklar.|
|[Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)|VSTO eklentileri ve ilgili programlama görevlerinin programlama modeline genel bir bakış sağlar.|
|[Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)|Belge düzeyi özelleştirmelerinin ve ilgili programlama görevlerinin programlama modeline genel bir bakış sağlar.|
|[Office UI özelleştirmesi](../vsto/office-ui-customization.md)|Office uygulamalarının Kullanıcı arabirimini VSTO eklentileri ve belge düzeyi özelleştirmeleri kullanarak özelleştirebilmeniz için kullanabileceğiniz farklı yollar açıklanmaktadır.|
|[Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)|Verileri denetimlere bağlama ve belge düzeyi özelleştirmelerde verileri önbelleğe alma gibi Office çözümlerinde verilerle çalışmanıza yönelik farklı yollar açıklanmaktadır.|
|[Otomatik kaydetme Office çözümlerini nasıl etkiler](./how-autosave-impacts-office-solutions.md)|Otomatik kaydetme etkinleştirildiğinde Office çözümlerinde yapmanız gerekebilecek ayarlamaları açıklar.|
|[Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)|Office çözümleri oluştururken karşılaşabileceğiniz yaygın sorunları çözmek için ipuçları sağlar.|
|[Office 'te iş parçacığı desteği](../vsto/threading-support-in-office.md)|Office çözümlerinde birden çok iş parçacığı ile çalışmaya genel bakış sunar.|
|[Office projelerinde erişilebilirlik](../vsto/accessibility-in-office-projects.md)|Office çözümlerinde bulunan erişilebilirlik özelliklerini açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Nasıl yapılır: belge özelliklerinden okuma ve yazma](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Nasıl yapılır: Office çok dilli kullanıcı arabirimini hedefleme](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [İzlenecek yol: Excel için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [İzlenecek yol: Outlook için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [İzlenecek yol: PowerPoint için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [İzlenecek yol: proje için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [İzlenecek yol: Word için ilk VSTO eklentisini oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

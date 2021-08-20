---
title: Office çözümleri geliştirme
description: Visual Studio Office geliştirici araçlarını kullanarak proje tasarlamayı öğrenin. Ayrıca, kodu ve özel kullanıcı arabirimini (UI) uygulamaya nasıl başlayacağınızı öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f9bc17fddd98132d95a994483afb3e3d3a6e6801
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148278"
---
# <a name="develop-office-solutions"></a>Office çözümleri geliştirme
  Visual Studio ' de Office geliştirici araçlarını kullanarak bir proje tasarladıktan ve proje dosyalarını ayarladıktan sonra, kodu ve özel kullanıcı arabirimini (uı) uygulamaya odaklanabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Office solutions programlama modeli
 Office nesne modeli, programlama yapacağımız çeşitli nesneleri kullanıma sunar. yönetilen kod kullanarak çözümler Office her seferinde, Office birincil birlikte çalışma derlemelerindeki türleri kullanan kodu yazarsınız. Visual Studio ' de Office proje şablonlarını kullanarak oluşturduğunuz çözümlerde, doğrudan projenizdeki oluşturulan sınıflara karşı kodu de yazabilirsiniz. daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Office çözümlerin farklı türlerini programla
 Oluşturmakta olduğunuz çözüm türü, projenizde hangi özellikleri kullanabileceğinizi belirler. örneğin, tasarım zamanında Visual Studio ' deki **araç kutusundan** öğeleri sürükleyerek belge düzeyi özelleştirmelere Windows Forms denetimleri ve genişletilmiş Office denetimleri ( *konak denetimleri* olarak adlandırılır) ekleyebilirsiniz. ancak, VSTO eklenti geliştiriyorsanız bu denetim türlerini yalnızca çalışma zamanında belgelere kod yazarak ekleyebilirsiniz.

 Farklı çözüm türlerine özgü özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Program VSTO](../vsto/programming-vsto-add-ins.md)eklentileri.

- [Program belge düzeyinde özelleştirmeler](../vsto/programming-document-level-customizations.md).

- [Office uı özelleştirmesi](../vsto/office-ui-customization.md).

  proje oluşturmanıza yardımcı olmak üzere Office çözümlerini ve yordamlarını planlamaya yardımcı olacak arka plan bilgileri için, bkz. [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)|Office çözümlerinde kod yazmanın farklı yönlerini açıklar.|
|[Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)|VSTO eklentileri ve ilgili programlama görevlerinin programlama modeline genel bir bakış sağlar.|
|[Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)|Belge düzeyi özelleştirmelerinin ve ilgili programlama görevlerinin programlama modeline genel bir bakış sağlar.|
|[Office UI özelleştirmesi](../vsto/office-ui-customization.md)|VSTO eklentileri ve belge düzeyi özelleştirmeleri kullanarak Office uygulamalarının kullanıcı arabirimini özelleştirebilmeniz için farklı yollar açıklanmaktadır.|
|[Office çözümlerinde veri](../vsto/data-in-office-solutions.md)|verileri denetimlere bağlama ve belge düzeyi özelleştirmelerde verileri önbelleğe alma gibi Office çözümlerinde verilerle çalışmanıza olanak tanıyan farklı yollar açıklanmaktadır.|
|[otomatik kaydetme, çözümleri Office nasıl etkiler](./how-autosave-impacts-office-solutions.md)|otomatik kaydetme etkinleştirildiğinde Office çözüm yapmanız gerekebilecek ayarlamaları açıklar.|
|[Office çözümlerinde sorun giderme](../vsto/troubleshooting-office-solutions.md)|Office çözümleri oluştururken karşılaşabileceğiniz yaygın sorunları çözmek için ipuçları sağlar.|
|[Office iş parçacığı desteği](../vsto/threading-support-in-office.md)|Office çözümlerinde birden çok iş parçacığı ile çalışmaya genel bir bakış sağlar.|
|[Office projelerinde erişilebilirlik](../vsto/accessibility-in-office-projects.md)|Office çözümlerinde kullanılabilen erişilebilirlik özelliklerini açıklar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Nasıl yapılır: belge özelliklerinden okuma ve yazma](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [nasıl yapılır: Office çok dilli kullanıcı arabirimini hedefleme](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [izlenecek yol: Excel için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [izlenecek yol: Outlook için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [izlenecek yol: PowerPoint için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [izlenecek yol: Project için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [izlenecek yol: Word için ilk VSTO eklentiyi oluşturma](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)

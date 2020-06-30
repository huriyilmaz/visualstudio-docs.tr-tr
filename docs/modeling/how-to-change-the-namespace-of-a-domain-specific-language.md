---
title: 'Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme'
ms.date: 10/31/2018
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, namespace
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ff7c73694cb53f7fbea21514feeaab4abce3f29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542681"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme

Etki alanına özgü dilin ad alanını değiştirebilirsiniz. DSL **Gezgini**' nde, DSL paketi projesinin özelliklerinde ve derleme bilgilerinde değişiklik yapın.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü dilin ad alanını değiştirmek için

1. **DSL Gezgini**' nde **DSL** düğümünü seçin.

2. **Özellikler** penceresinde **ad alanı** özelliğini değiştirin.

3. Çözümü kaydedin ve şablonları dönüştürün.

4. **Proje** menüsünde **DSL özellikleri**' ni seçin.

   Projenizin özellikleri görüntülenir.

5. **Uygulama** sekmesini seçin.

6. **Varsayılan ad alanı** özelliğini yeni ad alanı adı olarak değiştirin.

7. Derlemenin adını da değiştirmek istiyorsanız, **derleme adı özelliğini değiştirin.**

8. Derleme adını değiştirdiyseniz Dslpackage\package.exe ' i açın ve bu satırı güncelleştirin:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdıysanız, kod dosyalarındaki ad alanını ve sınıf başvurularını değiştirdiğinizden emin olun.

10. Visual Studio Deneysel örneğini sıfırlayın.

    1. **\Users \\ **_{Name}_**\appdata\local\microsoft\visualstudio \\ \* Exp**öğesini silin.

    2. Windows **Başlat** menüsünde **tüm programlar**' ı seçin  >  **Microsoft Visual Studio 2010 SDK**  >  **araçları**  >  **deneysel örneği sıfırlayın**.

11. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
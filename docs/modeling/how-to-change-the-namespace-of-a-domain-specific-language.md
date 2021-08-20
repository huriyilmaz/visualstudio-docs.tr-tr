---
title: 'Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme'
description: Etki alanına özgü dilin ad alanını değiştirme hakkında bilgi sağlar.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 66ce1219f3a18c65e23c2ddc420449a0d8bc7b3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157494"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme

Etki alanına özgü dilin ad alanını değiştirebilirsiniz. DSL **Gezgini**' nde, DSL paketi projesinin özelliklerinde ve derleme bilgilerinde değişiklik yapın.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü dilin ad alanını değiştirmek için

1. **DSL Gezgini**' nde **DSL** düğümünü seçin.

2. **Özellikler** penceresinde **ad alanı** özelliğini değiştirin.

3. Çözümü kaydedin ve şablonları dönüştürün.

4. **Project** menüsünde **Dsl özellikleri**' ni seçin.

   Projenizin özellikleri görüntülenir.

5. **Uygulama** sekmesini seçin.

6. **Varsayılan ad alanı** özelliğini yeni ad alanı adı olarak değiştirin.

7. Derlemenin adını da değiştirmek istiyorsanız, **derleme adı özelliğini değiştirin.**

8. Derleme adını değiştirdiyseniz Dslpackage\package.exe ' i açın ve bu satırı güncelleştirin:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdıysanız, kod dosyalarındaki ad alanını ve sınıf başvurularını değiştirdiğinizden emin olun.

10. Visual Studio deneysel örneği sıfırlayın.

    1. **\Users \\**_{Name}_**\appdata\local\microsoft\visualstudio \\ \* Exp** öğesini silin.

    2. Windows **başlat** menüsünde **tüm programlar**' ı seçin  >  **Microsoft Visual Studio 2010 SDK**  >  **araçları**  >  **deneysel örneği sıfırlayın**.

11. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))
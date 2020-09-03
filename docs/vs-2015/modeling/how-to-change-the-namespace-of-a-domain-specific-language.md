---
title: 'Nasıl yapılır: etki alanına özgü dilin ad alanını değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b61b248876f701e9d5286063f28b4f71d73e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671728"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilin Ad Alanını Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etki alanına özgü dilin ad alanını değiştirebilirsiniz. Bu değişikliği DSL paketinin özelliklerinde ve derleme bilgilerinde, **DSL Gezgini**'nde yapmanız gerekir.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü dilin ad alanını değiştirmek için

1. **DSL Gezgini**' nde **DSL** düğümüne tıklayın.

2. **Özellikler** penceresinde **ad alanı** özelliğini değiştirin.

3. Çözümü kaydedin ve şablonları dönüştürün.

4. **Proje** menüsünde **DSL özellikleri**' ne tıklayın.

     Projenizin özellikleri görüntülenir.

5. **Uygulama** sekmesine tıklayın.

6. **Varsayılan ad alanı** özelliğini yeni ad alanı adı olarak değiştirin.

7. Derlemenin adını da değiştirmek istiyorsanız, **derleme adı özelliğini değiştirin.**

8. Derleme adını değiştirdiyseniz Dslpackage\package.exe ' i açın ve bu satırı güncelleştirin:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdıysanız, kod dosyalarındaki ad alanını ve sınıf başvurularını değiştirdiğinizden emin olun.

10. Visual Studio Deneysel örneğini sıfırlayın.

    1. **\Users \\ **_{Name}_**\appdata\local\microsoft\visualstudio \\ \* Exp** silme

    2. Windows **Başlat** menüsünde **tüm programlar**, **Microsoft Visual Studio 2010 SDK**, **Araçlar**, **deneysel örneği Sıfırla**' yı seçin.

11. **Derle** menüsünde **çözümü yeniden derle**' yi seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

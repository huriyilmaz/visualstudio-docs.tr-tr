---
title: 'Nasıl kullanılır: Etki alanına özgü bir dilin ad alanını değiştirme'
description: Etki alanına özgü bir dilin ad alanını değiştirme hakkında bilgi sağlar.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: db9043c2a4c5abd19c839d2586709412d7607019
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387313"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Nasıl kullanılır: Etki alanına özgü bir dilin ad alanını değiştirme

Etki alanına özgü bir dilin ad alanını değiştirebilirsiniz. **DSL Gezgini'nde, Dsl** Paketi projesinin özelliklerinde ve derleme bilgisinde değişikliğini yapmak.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Etki alanına özgü bir dilin ad alanını değiştirmek için

1. **DSL Gezgini'nde** Dsl **düğümünü** seçin.

2. Özellikler **penceresinde** Namespace **özelliğini** değiştirin.

3. Çözümü kaydedin ve şablonları dönüştürin.

4. Proje menüsünde **Dsl** **Özellikleri'ne tıklayın.**

   Projenizin özellikleri görüntülenir.

5. Uygulama **sekmesini** seçin.

6. Varsayılan ad **alanı özelliğini** yeni ad alanı adıyla değiştirme.

7. Derlemenin adını da değiştirmek için Derleme adı **özelliğini de değiştirebilirsiniz.**

8. Derleme adını değiştirdiysanız DslPackage\Package.tt açın ve şu satırı güncelleştirin:

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Herhangi bir özel kod yazdınız, kod dosyalarındaki ad alanı ve sınıf başvurularını değiştir emin olun.

10. Deneysel Visual Studio sıfırlayın.

    1. **\Users \\**_{your name}_**\AppData\Local\Microsoft\VisualStudio Exp öğesini \\ \* silin.**

    2. Windows Başlat menüsünde **Tüm** Programlar ve   >  **2010 SDK Microsoft Visual Studio** Deneysel Örneği  >    >  **Sıfırla'yı seçin.**

11. Derleme menüsünde **Çözümü Yeniden** **Oluştur'a tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil araçları sözlüğü](/previous-versions/bb126564(v=vs.100))
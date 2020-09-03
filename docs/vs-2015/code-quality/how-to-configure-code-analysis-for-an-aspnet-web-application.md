---
title: 'Nasıl yapılır: ASP.NET Web uygulaması için kod analizini yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657458"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Nasıl yapılır: Bir ASP.NET Web Uygulaması İçin Kod Analizini Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve ' de, [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] Web uygulamasına uygulanacak kod analizi *kural kümeleri* listesinden seçim yapabilirsiniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Varsayılan kural kümesi, en az Microsoft tarafından önerilen kurallardır. Web sitesi için uygulanacak başka bir kural kümesi seçebilirsiniz.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Bir ASP.NET Page Framework projesi için bir kural kümesi yapılandırmak için

1. **Çözüm Gezgini**Web sitesini seçin.

2. **Çözümle** menüsünde, **Web sitesi Için kod analizini Yapılandır**' ı tıklatın.

3. Çözümü seçtiyseniz ve çözümde birden fazla proje varsa, **yapılandırma** ve **Platform** listelerinden yapı yapılandırması ve hedef işletim sistemini seçin.

4. Çözümdeki her proje için **kural kümesi** sütununa tıklayın ve sonra çalıştırılacak kural kümesinin adına tıklayın.

5. Varsayılan olarak, çözüm içindeki tüm projelerde kod analizi çalıştırılır. Belirli bir proje için kod analizini devre dışı bırakmak veya etkinleştirmek için şu adımları izleyin:

    1. Proje adına sağ tıklayın ve ardından Özellikler ' e tıklayın.

    2. **Kod analizini etkinleştir** onay kutusunu işaretleyin veya temizleyin. Ayrıca, **Çözümle** menüsünde **Web sitesinde Kod analizini Çalıştır '** i seçerek Kod analizini el ile de çalıştırabilirsiniz.

6. **Bu kural kümesini Çalıştır** açılan listesinde, aşağıdaki adımları izleyin:

    - Kullanmak istediğiniz kural kümesini seçin.

    - **\<Browse>** Listede olmayan mevcut bir özel kural kümesini belirtmek için seçin.

    - Özel bir kural kümesi tanımlayın. Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).

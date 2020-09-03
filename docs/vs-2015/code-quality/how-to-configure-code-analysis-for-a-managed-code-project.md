---
title: 'Nasıl yapılır: yönetilen kod projesi için kod analizini yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658852"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Nasıl yapılır: Yönetilen Kod Projesi İçin Kod Analizini Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve ' de, [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] bir yönetilen kod projesine uygulamak için kod analizi *kural kümeleri* listesinden seçim yapabilirsiniz. Varsayılan kural kümesi, en düşük Microsoft önerilen kurallardır. Bir projeye veya bir Çözümdeki tüm projelere başka bir kural kümesi uygulayabilirsiniz.

> [!NOTE]
> ASP.NET Web uygulamaları için bir kural kümesinin nasıl yapılandırılacağı hakkında bilgi için bkz. [nasıl yapılır: bir ASP.NET Web uygulaması Için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Bir .NET Framework projesi için bir kural kümesi yapılandırmak için

1. **Çözüm Gezgini**, projeye tıklayın.

2. **Çözümle** menüsünde, *ProjectName* **için kod analizini Yapılandır** ' ı tıklatın.

3. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platformu ' na tıklayın.

4. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için **derlemede Kod analizini etkinleştir (CODE_ANALYSIS sabiti tanımlar)** onay kutusunu seçin. Ayrıca, **Çözümle** menüsünü açıp *ProjectName* **üzerinde Kod analizini Çalıştır '** a tıklayarak Kod analizini el ile de çalıştırabilirsiniz.

5. Varsayılan olarak, kod analizi dış araçlar tarafından otomatik olarak oluşturulan koddan uyarı raporlamaz. Oluşturulan koddan gelen uyarıları görüntülemek için, **oluşturulan koddan sonuçları bastır** onay kutusunun işaretini kaldırın.

    > [!NOTE]
    > Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

6. **Bu kural kümesini Çalıştır** listesinde aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz kural kümesine tıklayın.

    - **\<Browse...>** Listede olmayan mevcut bir özel kural kümesini belirtmek için tıklayın.

    - Özel bir kural kümesi tanımlayın.

         Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [İzlenecek Yol: Özel bir Kural Kümesini Yapılandırma ve Kullanma](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)

---
title: 'Nasıl yapılır: bir çözümde birden çok proje için yönetilen kod kural kümelerini belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656417"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Nasıl Yapılır: Bir Çözümde Birden Çok Proje İçin Yönetilen Kod Kural Kümesi Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, bir çözümün tüm yönetilen projelerine, Microsoft 'un önerilen en düşük kural kodu çözümleme *kuralı kümesi*atanır. Çözümün projelerine atanmış kural kümelerini çözüm için Özellikler iletişim kutusunda değiştirebilirsiniz.

> [!NOTE]
> Varsayılan olarak, proje kodu Analizi derleme adımı olarak çalıştırılmaz. Derleme adımı olarak kod analizini etkinleştirmek için bkz. [nasıl yapılır: yönetilen kod projesi Için kod analizini yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Yönetilen kod çözümünde birden çok proje için kural kümesi belirtme

1. @No__t_0. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] veya [!INCLUDE[vsPro](../includes/vspro-md.md)] çözümü açın.

2. **Çözümle** menüsünde, **çözüm Için kod analizini Yapılandır**' ı tıklatın.

3. Gerekirse, **ortak özellikler**' i genişletin ve ardından **Kod Analizi ayarları**' na tıklayın.

4. Bir veya daha fazla proje için bir kural kümesi belirtebilirsiniz.

    - Tek bir proje için bir kural kümesi belirtmek üzere proje adına tıklayın.

    - Birden çok proje için bir kural kümesi belirtmek için CTRL tuşunu basılı tutun ve proje adlarına tıklayın.

    - Çözümdeki tüm projeleri belirtmek için SHIFT tuşunu basılı tutun ve proje listesine tıklayın.

5. Projenin **kural kümesi** alanına tıklayın ve ardından uygulamak istediğiniz kural kümesinin adına tıklayın.

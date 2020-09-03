---
title: Kod ölçümleri sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672449"
---
# <a name="troubleshooting-code-metrics-issues"></a>Kod Ölçümleri Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod ölçümleri topladığınızda aşağıdaki sorunlardan bazılarını yaşayabilirsiniz:

- [Visual Studio 2010 kod karmaşıklığı hesaplamalarında yapılan değişiklikler](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Visual Studio 2010 kod karmaşıklığı hesaplamalarında yapılan değişiklikler
 Aynı işlev için, içinde hesaplanan kod karmaşıklığı ölçümü [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] aşağıdaki durumlar için önceki sürümleri tarafından hesaplanan ölçüden farklı olabilir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] :

- İşlev bir veya daha fazla catch bloğu içeriyor. Önceki sürümlerinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , catch blokları hesaplamaya eklenmedi. [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]' De, her bir catch bloğunun karmaşıklığı işlevin karmaşıklığına eklenir.

- İşlev, bir anahtar (VB 'de Case, Select Case) ifadesini içerir. [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]Ve önceki sürümler arasındaki derleyici farklılıkları, daha fazla dönüş durumu içeren bazı Switch deyimleri için farklı MSIL kodu oluşturabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

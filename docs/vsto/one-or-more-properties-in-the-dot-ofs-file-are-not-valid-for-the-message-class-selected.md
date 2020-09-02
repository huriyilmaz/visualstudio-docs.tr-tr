---
title: .ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli değil
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d58ad6ff89d8cf41ec60135cfbfe3deac1382f1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977867"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs dosyasındaki bir veya daha fazla özellik seçilen ileti sınıfı için geçerli değil
  Outlook 'ta tasarlanan bir form bölgesini içeri aktardığınızda bu hata görüntülenir, ancak form bölgesindeki bir veya daha fazla alan **Yeni form bölgesi** sihirbazının son sayfasında seçtiğiniz ileti sınıflarıyla uyumlu değildir.

Örneğin, **görev (IPM) öğesini seçebilirsiniz. Görev)** **Yeni form bölgesi** sihirbazının son sayfasında. Form bölgesinin bir **Iş adresi** alanı varsa, bir görevin iş adresi olmadığı için bu hatayı alırsınız. Bu nedenle, **Iş adresi** alanı `IPM.Task` ileti sınıfıyla uyumlu değildir.

 **Görev (IPM) seçeneğini belirleyebilirsiniz. Görev)** **Yeni form bölgesi** sihirbazının son sayfasında. Form bölgesinin bir **Iş adresi** alanı varsa, bir görevin iş adresi olmadığı için bu hatayı alırsınız. Bu nedenle, **Iş adresi** alanı `IPM.Task` ileti sınıfıyla uyumlu değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Yeni form bölgesi** Sihirbazı ' nın son sayfasında, form bölgesindeki alanlarla uyumlu bir ileti sınıfı seçin.

- Outlook 'taki form tasarımcısında, ileti sınıflarıyla uyumlu olmayan alanları kaldırın. **Yeni form bölgesi** sihirbazının son sayfasında seçimi planladığınız alanları kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)

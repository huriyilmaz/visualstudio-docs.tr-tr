---
title: Kod için Otomasyon sağlama | Microsoft Docs
description: İç veri yapınız tarafından belirlenen arabirimlerin uygulanması için bir kod modeli uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57d5337ae088560bb94a6af39902e90b6af02686
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060971"
---
# <a name="providing-automation-for-code"></a>Kod için Otomasyon Sağlama
Kodunuz için bir otomasyon modeli oluşturmak gerekli değildir. Ortam SDK 'Sı bu işlemi gerçekleştirmek için bir örnek sağlamaz. Kod modellerine ilişkin Öngörüler için, nesnesine bakın <xref:EnvDTE.CodeModel> .

 Bir kod modeli uygulamak için, iç veri yapınız tarafından belirlenen arabirimleri uygulamanız gerekir. Nesneler `IDispatch` sınıfından türetilmelidir.

 Genişletmediğiniz nesneler <xref:EnvDTE.CodeModel> ve <xref:EnvDTE.FileCodeModel> <xref:EnvDTE.Project> nesnesinden kullanılabilir ve aşağıdaki gibi görünür:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 `CodeModel` `FileCodeModel` `Project` Ve nesnelerinizin döndürdüğü nesnede yalnızca veya arabirimini uygulamayı seçebilirsiniz <xref:EnvDTE.ProjectItem> . Bu arabirimden proje sisteminiz için uygun olan tüm işlevleri sağlayın.

 Standart ve arabirimlerde kullanılamayan Yöntemler veya özellikler gibi özellikler eklemek istiyorsanız, `CodeModel` `FileCodeModel` Standart 'dan devralan kendi arabirimini oluşturun. Son kullanıcıların bunu arayacağı bilmesini sağlamak için, bunu proje sisteminizle birlikte belgelediğinizden emin olun. Standart arabirimini döndürürler, ancak Kullanıcı, varsa, `QueryInterface` Bu yöntemi çağırabilir veya varsa arayüzüne çevirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)

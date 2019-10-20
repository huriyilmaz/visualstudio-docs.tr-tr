---
title: 'CA1824: derlemeleri NeutralResourcesLanguageAttribute ile Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: efa328fdff9c357e0183fc2ca80e4d77d4f6782e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661111"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Derlemeleri NeutralResourcesLanguageAttribute ile işaretleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir derleme, **resx**tabanlı bir kaynak içerir ancak buna <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> uygulanmaz.

## <a name="rule-description"></a>Kural Tanımı
 **NeutralResourcesLanguage** özniteliği, bir derleme için nötr kültürün kaynaklarını göstermek için kullanılan dilin **ResourceManager** değerini bilgilendirir. Aynı kültürden kaynakları bağımsız kaynaklar diliyle ararken **ResourceManager** otomatik olarak ana derlemede bulunan kaynakları kullanır. Geçerli iş parçacığı için geçerli kullanıcı arabirimi kültürüne sahip bir uydu derlemesini aramak yerine bunu yapar. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir.

## <a name="fixing-violations"></a>Ihlaller düzeltiliyor
 Bu kural ihlalini onarmak için, derlemeye özniteliği ekleyin ve nötr kültürün kaynak dilini belirtin.

## <a name="specifying-the-language"></a>Dili belirtme

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Bağımsız kültür kaynağının dilini belirtmek için

1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. Sol gezinti çubuğundan **uygulama**' yı seçin ve ardından **derleme bilgileri**' ne tıklayın.

3. **Derleme bilgileri** iletişim kutusunda, **nötr dil** açılan listesinden dili seçin.

4. **Tamam**'a tıklayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarı gösterilmemek için izin verilir. Ancak, başlangıç performansı düşebilir.

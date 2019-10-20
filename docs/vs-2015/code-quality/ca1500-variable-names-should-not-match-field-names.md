---
title: 'CA1500: değişken adları alan adlarıyla eşleşmemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b46594a53e6562c2c6a069a9a25d58b3e32865eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607936"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Değişken adları alan adlarıyla eşleşmemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1500: değişken adları alan adlarıyla eşleşmemelidir](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Bir alanla aynı ada sahip bir parametre üzerinde harekete geçirildiğinde:<br /><br /> -Parçalama-Eğer parametreyi bildiren alan ve yöntem, yaptığınız değişiklikten bağımsız olarak, derleme dışında görülemez.<br />-Parçalama-alanın adını değiştirirseniz ve derleme dışında görünebilirler.<br />-Parçalama-parametrenin adını ve bunu bildiren yöntemi derleme dışında görülebilir.<br /><br /> Bir alanla aynı ada sahip yerel bir değişkende harekete geçirildiğinde:<br /><br /> -Bölünmez-siz yaptığınız değişiklikten bağımsız olarak, alan derleme dışında görülemez.<br />-Kırılmamış-yerel değişkenin adını değiştirirseniz ve alanın adını değiştirmeyin.<br />-Parçalama-alanın adını değiştirirseniz ve derleme dışında görünebilirler.|

## <a name="cause"></a>Sebep
 Örnek yöntemi bir parametre ya da adı bildirim türünün bir örnek alanıyla eşleşen yerel bir değişken bildirir. Kuralı ihlal eden yerel değişkenleri yakalamak için, sınanan derlemenin hata ayıklama bilgileri kullanılarak oluşturulması gerekir ve ilişkili program veritabanı (. pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural Tanımı
 Bir örnek alanının adı bir parametre veya yerel değişken adıyla eşleştiğinde, Yöntem gövdesinin içindeyken örnek alana `this` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Me`) anahtar sözcüğü kullanılarak erişilir. Kodu koruma sırasında, bu farkı unutmak kolaydır ve parametre/yerel değişkenin, hatalara yol eden örnek alana başvurduğunu varsayın. Bu, özellikle uzun yöntem gövdeleri için geçerlidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için parametreyi/değişkeni ya da alanını yeniden adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralın iki ihlalini gösterir.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

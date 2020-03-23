---
title: ÇözümanahtarıKaynak Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa4e2454a0216e697ed12404091eb0ef16416cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632712"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource görevi

Güçlü ad anahtar kaynağını belirler.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `ResolveKeySource` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|İsteğe bağlı `Int32` parametre.<br /><br /> Geri sayım iletisini görüntülemek için saniyeler içinde süreyi alır veya ayarlar.|
|`AutoClosePasswordPromptTimeout`|İsteğe bağlı `Int32` parametre.<br /><br /> Parola istemi iletişim kutusunu kapatmadan önce beklemesi gereken süreyi saniyeler içinde alır veya ayarlar.|
|`CertificateFile`|İsteğe bağlı `String` parametre.<br /><br /> Sertifika dosyasının yolunu alır veya ayarlar.|
|`CertificateThumbprint`|İsteğe bağlı `String` parametre.<br /><br /> Sertifikanın parmak izini alır veya ayarlar.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Anahtar dosyasının yolunu alır veya ayarlar.|
|`ResolvedKeyContainer`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Çözülmüş anahtar kapsayıcısını alır veya ayarlar.|
|`ResolvedKeyFile`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Çözülmüş anahtar dosyasını alır veya ayarlar.|
|`ResolvedThumbprint`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Çözülmüş sertifika parmak izini alır veya ayarlar.|
|`ShowImportDialogDespitePreviousFailures`|İsteğe bağlı `Boolean` parametre.<br /><br /> If, `true`önceki hatalara rağmen içe aktarma iletişim kutusunu göster.|
|`SuppressAutoClosePasswordPrompt`|İsteğe bağlı `Boolean` parametre.<br /><br /> Parola istemi iletişim kutusunun otomatik olarak kapatılmaması gerektiğini belirten bir Boolean değeri alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)

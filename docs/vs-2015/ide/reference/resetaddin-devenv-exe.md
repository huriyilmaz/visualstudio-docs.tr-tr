---
title: -Resetaddın (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665596"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen eklenti ile ilişkili komutları ve komut Kullanıcı arabirimini kaldırır.

## <a name="syntax"></a>Söz dizimi

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Bağımsız değişkenler
 `AddIn` Seçim. Eklentinin komut adı.

## <a name="remarks"></a>Açıklamalar
 Varsayılan olarak, eklentinin komut adı öğesine eşittir *\<AddInSolutionName>* . <em>. \<AddInSolutionName> </em>Ve, yönteminin parametresi olarak Connect.cs içinde görüntülenir `commandName` `Exec` . Ayrıca, Visual Studio 'daki Komutlar penceresine eklentinin adını yazarak ve REST 'i doldurmanız için IntelliSense kullanarak komut adını doğrulayabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, Visual Studio 'Yu başlatır ve `MyAddin` eklentinin başlangıçta çalıştırılmasını önler.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv komut satırı anahtarlarında](../../ide/reference/devenv-command-line-switches.md) geliştirme ayarlarını özelleştirme

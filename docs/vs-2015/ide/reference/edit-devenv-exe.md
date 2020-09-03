---
title: -Düzenle (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c81f59f2dadf535af4e9a76949a29fd1355c33f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657750"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen dosyayı varolan bir örneğinde açar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="syntax"></a>Söz dizimi

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `file1` Seçim. Var olan bir örneğinde açılacak dosya [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Mevcut bir örneği yoksa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , Basitleştirilmiş pencere düzeniyle yeni bir örnek oluşturulur ve `file1` Yeni örnekte açılır.

 `file2` Seçim. Mevcut örneğinde açmak için bir veya daha fazla ek dosya [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="remarks"></a>Açıklamalar
 Dosya belirtilmemişse ve var olan bir örneği varsa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , var olan örneği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odak alır. Hiçbir dosya belirtilmemişse ve mevcut bir örneği yoksa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , yeni bir örneği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Basitleştirilmiş pencere düzeniyle oluşturulur.

 Mevcut örneği [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kalıcı bir durumdaysa, örneğin, [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açıksa, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kalıcı durumdan çıkıldığında dosya mevcut örnekte açılır.

## <a name="example"></a>Örnek
 Bu örnek, dosyayı `MyFile.cs` var olan bir örneğinde açar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] veya zaten mevcut değilse dosyayı yeni bir örneğinde açar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)

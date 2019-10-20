---
title: -Düzenle (devenv. exe) | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657750"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen dosyayı varolan bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneğinde açar.

## <a name="syntax"></a>Sözdizimi

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `file1`. @No__t_0 var olan bir örneğinde açılacak dosya. @No__t_0 örneği yoksa, Basitleştirilmiş bir pencere düzeniyle yeni bir örnek oluşturulur ve `file1` yeni örnekte açılır.

 Isteğe bağlı `file2`. Mevcut [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneğinde açmak için bir veya daha fazla ek dosya.

## <a name="remarks"></a>Açıklamalar
 Dosya belirtilmemişse ve var olan bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneği varsa, var olan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneği odağı alır. Hiçbir dosya belirtilmemişse ve mevcut bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneği yoksa, Basitleştirilmiş bir pencere düzeniyle yeni bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneği oluşturulur.

 Mevcut [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneği kalıcı durumdaysa, örneğin [Seçenekler iletişim kutusu](../../ide/reference/options-dialog-box-visual-studio.md) açıksa, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kalıcı durumdan çıktığında dosya mevcut örnekte açılır.

## <a name="example"></a>Örnek
 Bu örnek, dosya `MyFile.cs` var olan bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneğinde açar veya zaten mevcut değilse dosyayı yeni bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] örneğinde açar.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)

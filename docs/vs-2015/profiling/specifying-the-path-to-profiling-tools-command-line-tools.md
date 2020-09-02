---
title: Komut satırı araçlarının Profil Oluşturma Araçları yolunu belirtme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fadcff84c4b927a7718d7d4ad1311918ae0f18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199786"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Profil Oluşturma Araçları Komut Satırı Araçları Yolunu Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Profil oluşturma araçları komut satırı araçlarının yolu, PATH ortam değişkenine eklenmez. 32 bit bilgisayarlarda, Araçlar tek bir dizindir. 64 bit bilgisayarlarda profil oluşturma araçlarının 32-bit ve 64 bit sürümleri vardır.  
  
## <a name="32-bit-computers"></a>32 bit bilgisayarlar  
 32 bit bilgisayarlarda, varsayılan profil oluşturucu araçları dizini *, \Program Files\Microsoft*Visual Studio 11.0 \ Team Tools\performance Tools dizinidir.  
  
## <a name="64-bit-computers"></a>64 bit bilgisayarlar  
 64 bit bilgisayarlarda, profili oluşturulmuş uygulamanın hedef platformuna göre yolunu belirtin.  
  
- 32 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:  
  
     *Sürücü*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\performans araçları  
  
- 64 bitlik uygulamalar için varsayılan profil oluşturucu araçları dizini:  
  
     *Sürücü*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\performance Tools\x64

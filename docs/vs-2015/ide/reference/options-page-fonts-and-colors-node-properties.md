---
title: Seçenekler sayfası, yazı tipleri ve renkler düğüm özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662423"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Seçenekler Sayfası, Yazı Tipleri ve Renkler Düğümü Özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belge, **Seçenekler** Iletişim kutusunun **ortam** kategorisinde **yazı tipleri ve renkler** altında görünecek şekilde kaydedilen bir araç penceresi için yazı tipi ve renk özelliklerini açıklar. Bu, VSPackages 'nin yüklenip kaldırılması durumunda değişebilir, renklenebilir öğelerin gruplarının dinamik yapısını destekler.

 Aşağıdaki bölümde, kayıtlı pencere türüne ve her pencere için kullanılabilen özelliklere bir örnek gösterilmektedir.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Metin düzenleyici veya yazıcı veya diyaloglar ve araç pencereleri
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -veya-

 `DTE.Properties("FontsAndColors", "Printer")`

 -veya-

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (dize)|"Courier New" gibi kullanılacak yazı tipi adı.|
|Fontkarakterkümesi|Get/Set ( <xref:EnvDTE.vsFontCharSet> )|<xref:EnvDTE.vsFontCharSet>İbranice veya Rusça gibi kullanılacak karakter kümesi türünü belirten bir değer.|
|FontSize|Al/ayarla (kısa)|Kullanılacak yazı tipi boyutu (punto). Örneğin, 10 veya 12.|

## <a name="see-also"></a>Ayrıca Bkz.
 Seçenekler sayfa seçenekleri sayfasında [özellik öğelerinin adlarını belirleyen](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [seçenek ayarlarını denetleme](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [sayfası, ortam düğümü özellikleri](../../ide/reference/options-page-environment-node-properties.md) [Seçenekler sayfası, metin düzenleyici düğümü özellikleri](../../ide/reference/options-page-text-editor-node-properties.md)

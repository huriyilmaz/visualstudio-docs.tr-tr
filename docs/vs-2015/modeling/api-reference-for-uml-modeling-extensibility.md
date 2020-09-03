---
title: UML modelleme genişletilebilirliği için API başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672802"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>UML Genişletilebilirlik Modellemesi için API Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile oluşturduğunuz modelleri okumak ve değiştirmek için program kodu yazabilirsiniz. API başvurusu, bu konuda size yardımcı olacak belirli sınıflar hakkında bilgi sağlar. Daha fazla görev yönelimli bilgi için [UML modellerini ve diyagramlarını genişletme](../modeling/extend-uml-models-and-diagrams.md)altındaki konulara bakın. Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Bütünleştirilmiş Kodlar

|Bütünleştirilmiş Kod|Bunu yapmanıza izin verir|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-IUseCase, IAssociation gibi model öğelerini okuyun ve değiştirin.<br />-Öğeler arasındaki ilişkilere gidin.<br /><br /> Ad alanları ve türler, UML belirtiminde tanımlananlara karşılık gelir.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Model öğelerinin yeni örneklerini oluşturma<br />-Erişim ve şekilleri ve diyagramları değiştirme.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Için modelleme SDK 'sı IÇIN](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) API başvurusu

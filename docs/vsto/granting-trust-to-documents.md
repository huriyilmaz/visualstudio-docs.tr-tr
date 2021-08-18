---
title: Belgelere güven verme
description: Belge düzeyi bir projenin, bildirimleri bir sertifikayla imzalama veya güven istemine tıklama gibi uygulama düzeyi projelerle aynı güvenlik gereksinimlerine nasıl sahip olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0825b66bfa21df321232546a022f088f152281f1e34285ad04fedbbfcc6e10d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352038"
---
# <a name="grant-trust-to-documents"></a>Belgelere güven verme
  Belge düzeyi proje, uygulama düzeyi projelerle aynı güvenlik gereksinimlerine sahiptir: bildirimleri bir sertifikayla imzalama veya güven istemine tıklama. Ayrıca, belge veya çalışma kitabı güvenilen konum olarak belirlenmiş bir dizinde bulunmalıdır.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Güvenilen konumlar
 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]ve Office 2010 ' deki uygulamalar, kullanıcıların güvenilen konumlar gibi güvenlik ve gizlilik ayarlarını yapılandırabileceği güven merkezlerine sahiptir. Office çözümleri için, yerel bilgisayar güvenilen bir konum olarak kabul edilir. Ancak, daha yüksek risk nedeniyle, sistem için geçici klasörler, her bir Kullanıcı ve Internet Explorer için güvenli olmayan bazı dizinler vardır.

 güven merkezi hakkında daha fazla bilgi için [Office 2010 ' deki güvenlik ve ilkeler ve ayarlar](/previous-versions/office/office-2010/cc178946(v=office.14))bölümüne bakın. güvenilen klasörleri oluşturma, yönetme, kaldırma ve yapılandırma hakkında daha fazla bilgi için bkz. [2007 Office sisteminde güvenilen konumları ve güvenilir yayımcıları yapılandırma](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) ve [dosyalarınız için güvenilir bir konum oluşturma, kaldırma veya değiştirme](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Office çözümleri için güvenlik konuları
 Güvenilen konumlara hangi klasörlerin ekleneceğini göz önünde bulundurmanız gereken çeşitli güvenlik sorunları vardır:

- Yerel klasörler daha güvenli olduğu kabul edilir ve örtülü olarak güvenilirdir. Dosya paylaşımları gibi uzak konumların güvenilen konumlar olarak belirlenmesi gerekir.

- güvenilen konumlara bir dizin eklediğinizde, bu eylem yalnızca Office çözümlere değil, ayrıca VBA ve ActiveX kodu için de tam güven verir. Bu nedenle, kök dizin ve *Belgelerim klasörleri güvenilir* olarak atanmamalıdır.

- Belgenin kendisi güvenilir konumlar kullanılarak güvenilir olsa da, özelleştirmeye güvenmek için ek izinler gerekir. bir sertifikayla bildirimleri imzalarken, güven istemine tıklayarak veya Office çözümünü *Program Files* dizinine yükleyerek özelleştirmeye tam güven verebilirsiniz.

- Belge düzeyi çözümünün belge veya çalışma kitabını derlemeyle aynı dizinde veya farklı bir dizinde saklayabilirsiniz. örneğin, belge bir SharePoint sunucuda bulunabilir ve derleme bir ağ dosya paylaşımında bulunabilir. daha fazla bilgi için, bkz. [nasıl yapılır: belge düzeyi Office çözümünü SharePoint sunucusuna ClickOnce kullanarak yayımlama](/previous-versions/bb608595(v=vs.110)).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Office çözüm güvenliği sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
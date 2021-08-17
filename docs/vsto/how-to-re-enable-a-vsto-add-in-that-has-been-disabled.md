---
title: 'nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme'
description: Microsoft Office uygulamasında devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirmek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 02ba44eebff487c602acd3faaf6b65a89225a8a2547813ce055f66a2105883e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394218"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme
  Microsoft Office uygulamalar, beklenmedik şekilde davranan VSTO eklentileri devre dışı bırakabilir. bir uygulama, hata ayıklamaya çalıştığınızda VSTO eklentisini yüklemezse, uygulama VSTO eklentisinin etkin bir şekilde devre dışı bırakılmış veya geçici olarak devre dışı bırakılmış olabilir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>VSTO eklentileri sabit devre dışı bırakıldı
 VSTO eklentisi uygulamanın beklenmedik şekilde kapatılmasına neden olduğunda, sabit devre dışı bırakma gerçekleşebilir. ayrıca, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentisinin bir olay işleyicisi yürütülürken hata ayıklayıcıyı durdurursanız, geliştirme bilgisayarınızda da gerçekleşebilir.

### <a name="to-re-enable-a-vsto-add-in"></a>VSTO eklentisini yeniden etkinleştirmek için

1. Uygulamada, **Dosya** sekmesine tıklayın.

2. *ApplicationName* **seçenekleri** düğmesine tıklayın.

3. Kategoriler bölmesinde, **Eklentiler**' i tıklatın.

4. ayrıntılar bölmesinde, VSTO eklentisinin **devre dışı bırakılmış uygulama eklentileri** listesinde göründüğünü doğrulayın.

     **Ad** sütunu derlemenin adını belirtir ve **Location** sütunu uygulama bildiriminin tam yolunu belirtir.

5. **Yönet** kutusunda, **devre dışı öğeler**' i ve sonra **Git**' i tıklatın.

6. VSTO eklentisini seçin ve **etkinleştir**' e tıklayın.

7. **Kapat**’a tıklayın.

## <a name="soft-disabled-vsto-add-ins"></a>geçici devre dışı VSTO eklentileri
 VSTO eklentisi uygulamanın beklenmedik şekilde kapanmasına neden olmayan bir hata ürettiğinden, geçici devre dışı bırakma gerçekleşebilir. örneğin, bir uygulama, olay işleyicisi yürütülürken işlenmeyen bir özel durum oluşturursa VSTO eklentisini geçici olarak devre dışı bırakabilir <xref:Microsoft.Office.Tools.AddIn.Startup> .

> [!NOTE]
> geçici olarak devre dışı bir VSTO eklentisini yeniden etkinleştirdiğinizde, uygulama VSTO eklentisini hemen yüklemeye çalışır. başlangıçta uygulamanın VSTO eklentiyi geçici olarak devre dışı bırakmasına neden olan sorun düzeltilmediyse, uygulama VSTO eklentisini yeniden devre dışı bırakır.

### <a name="to-re-enable-a-vsto-add-in"></a>VSTO eklentisini yeniden etkinleştirmek için

1. Uygulamada, **Dosya** sekmesine tıklayın.

2. *ApplicationName* **seçenekleri** düğmesine tıklayın.

3. Kategoriler bölmesinde, **Eklentiler**' i tıklatın.

4. ayrıntılar bölmesinde, VSTO eklentisinin **etkin olmayan uygulama eklentileri** listesinde göründüğünü doğrulayın.

     **Ad** sütunu derlemenin adını belirtir ve **Location** sütunu uygulama bildiriminin tam yolunu belirtir.

5. **Yönet** kutusunda, **com eklentileri**' ne ve ardından **Git**' e tıklayın.

6. **COM eklentileri** iletişim kutusunda devre dışı VSTO eklentisinin yanındaki onay kutusunu işaretleyin.

7. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office projelerinde hata ayıklama](../vsto/debugging-office-projects.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)

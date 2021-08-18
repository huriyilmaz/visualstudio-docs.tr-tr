---
title: 'Nasıl: Devre dışı bırakılmış VSTO Eklentiyi yeniden etkinleştirme'
description: Visual Studio uygulamasında devre dışı bırakılmış bir VSTO eklentiyi yeniden etkinleştirmek için Microsoft Office öğrenin.
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
ms.openlocfilehash: ecaca6e262113ae4926ff21af5c468703fe78ae9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025985"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Nasıl: Devre dışı bırakılmış VSTO Eklentiyi yeniden etkinleştirme
  Microsoft Office uygulamaları beklenmedik VSTO eklentileri devre dışı bırakabilirsiniz. Bir uygulama hata ayıklamayı dene VSTO eklentinizi yükleyene kadar uygulama, Uygulama eklentinizi sabit olarak devre dışı bırakmış veya VSTO devre dışı bırakmış olabilir.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Sabit devre dışı VSTO Eklentileri
 Bir eklenti eklenti uygulamanın beklenmedik VSTO kapatmaya neden olduğunda sabit devre dışı bırakma oluşabilir. Hata ayıklayıcıyı, eklentinizin olay işleyicisi yürütmektedirken <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO bilgisayarınızda da oluşabilir.

### <a name="to-re-enable-a-vsto-add-in"></a>Bir Eklentiyi yeniden VSTO için

1. Uygulamada Dosya **sekmesine** tıklayın.

2. *ApplicationName Seçenekleri* **düğmesine** tıklayın.

3. Kategoriler bölmesinde **Eklentiler'e tıklayın.**

4. Ayrıntılar bölmesinde, VSTO Eklentinin Devre Dışı Uygulama Eklentileri **listesinde görüntülendiğinden emin** olur.

     **Ad** sütunu derlemenin adını, **Location** sütunu ise uygulama bildiriminin tam yolunu belirtir.

5. Yönet kutusunda **Devre** Dışı **Öğeler'e ve** ardından Git'e **tıklayın.**

6. Eklentiyi VSTO etkinleştir'e **tıklayın.**

7. **Kapat**’a tıklayın.

## <a name="soft-disabled-vsto-add-ins"></a>Eklentilerde VSTO devre dışı bırakıldı
 Eklentinin bir VSTO uygulamanın beklenmedik şekilde kapanmasını neden olmayan bir hata ürettiğinde, yazılım devre dışı bırakılama oluşabilir. Örneğin, bir uygulama, olay işleyicisi yürüt VSTO işleyicisi tarafından işsiz bir özel durum oluşturursa eklenti eklentisini geçici <xref:Microsoft.Office.Tools.AddIn.Startup> olarak devre dışı bırakabilirsiniz.

> [!NOTE]
> Eklentide bir yazılım devre dışı VSTO yeniden etkinleştirebilir, uygulama eklentiyi hemen VSTO çalışır. Başlangıçta uygulamanın eklentiyi geçici olarak devre dışı bırakmasına neden olan sorun VSTO düzeltilmiştir, uygulama eklentiyi yeniden VSTO devre dışı bıraktır.

### <a name="to-re-enable-a-vsto-add-in"></a>Bir Eklentiyi yeniden VSTO için

1. Uygulamada Dosya **sekmesine** tıklayın.

2. *ApplicationName Seçenekleri* **düğmesine** tıklayın.

3. Kategoriler bölmesinde **Eklentiler'e tıklayın.**

4. Ayrıntılar bölmesinde, VSTO Eklentinin Etkin Olmayan Uygulama Eklentileri **listesinde görüntülendiğinden emin** olur.

     **Ad** sütunu derlemenin adını, **Location** sütunu ise uygulama bildiriminin tam yolunu belirtir.

5. Yönet kutusunda **COM** **Eklentileri'ne ve ardından** Git'e **tıklayın.**

6. COM **Eklentileri iletişim kutusunda,** devre dışı bırakılmış eklentinin yanındaki onay kutusunu VSTO seçin.

7. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
- [Projelerde Office ayıklama](../vsto/debugging-office-projects.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)

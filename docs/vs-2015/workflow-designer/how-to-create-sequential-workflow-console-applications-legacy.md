---
title: 'Nasıl yapılır: sıralı Iş akışı konsol uygulamaları oluşturma (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662721"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Nasıl Yapılır: Sıralı İş Akışı Konsol Uygulamaları Oluşturma (Eski)
Tarafından sunulan eski ' i kullanarak sıralı bir Iş akışı konsol uygulaması projesi oluşturmak için bu adımları izleyin [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-sequential-workflow-console-application"></a>Sıralı bir iş akışı konsol uygulaması oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. Eski tasarımcıya erişmek için **Yeni proje** penceresinin en üstündeki aşağı açılan listeden **.NET Framework 3,0** seçeneğini veya **.NET Framework 3,5** seçeneğini seçin.

    > [!NOTE]
    > ' Deki varsayılan seçenek [!INCLUDE[vs2010](../includes/vs2010-md.md)] **.NET Framework 4**' dir. Bu seçenek [!INCLUDE[wf](../includes/wf-md.md)] , öğesini hedefleyen [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] ve eski tasarımcıyı kullanmayan uygulamalar oluşturmak için kullanılır.

4. **Proje türleri** bölmesinde, Visual C# projeleri ' ni veya Visual Basic projelerini ( **diğer diller**altında) seçin ve **iş akışı**' nı seçin.

5. **Şablonlar** bölmesinde **sıralı Iş akışı konsol uygulaması**' nı seçin.

6. **Ad** kutusuna projeniz için açıklayıcı bir ad girin ve kolayca tanımlanmasını sağlayın.

7. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

     Windows Form Tasarımcısı açılır ve oluşturduğunuz projenin Form1 ' i görüntülenir.

8. **Tamam**’a tıklayın.

     İş Akışı Tasarımcısı açılır ve oluşturduğunuz sıralı iş akışının iş akışı tasarım yüzeyini görüntüler.

9. **Araç kutusundan** bir etkinliği, **bırakma etkinliği** belirlenmiş alanındaki tasarım yüzeyine sürükleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Iş akışları geliştiren](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301) [eski Iş akışı projeleri oluşturma](../workflow-designer/creating-legacy-workflow-projects.md)
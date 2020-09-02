---
title: Birlikte Aç komutunu kullanarak dosyaları görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789362"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Birlikte Aç Komutunu Kullanarak Dosyaları Görüntüleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir proje IDE 'nin **birlikte Aç** iletişim kutusunu görüntülemesini isteyebilir. Bu istek, kullanıcıdan standart düzenleyiciler seçimine sahip bir dosyayı açmasını ister. Aşağıdaki adımlarda bu işlem açıklanır.  
  
1. Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , parametresi için OSE_UseOpenWithDialog değerini belirterek çağırır `OSEOpenDocEditor` .  
  
2. Belgenin dosya adı uzantısına bağlı olarak IDE, kayıt defterinde listelenen düzenleyicilerin belirtilen belgeyi açabildiğini belirler ve bu bilgileri **birlikte Aç** iletişim kutusunda görüntüler.  
  
    > [!NOTE]
    > **Birlikte Aç** iletişim kutusuna dahil olması gereken bir iç düzenleyiciye sahip olan projeler, her bir düzenleyici için bir düzenleyici fabrikası kaydetmelidir. İç düzenleyiciler yalnızca belirli bir proje türüyle birlikte çalışır ve bu yöntem, yöntemi uygulamasında zorlanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . IDE, çekirdek metin Düzenleyicisi ve ikili düzenleyici için yerleşik bir düzenleyici fabrikası içerir. IDE, kayıtlı her Windows dosya ilişkilendirmesi adına bir düzenleyici fabrikası örneği de oluşturur. Bu tür bir dosyaya örnek olarak Microsoft Word vardır.  
  
3. Kullanıcı **birlikte Aç** iletişim kutusundan bir öğe SEÇTIĞINDE, IDE yöntemi çağırarak belgeyi açar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)

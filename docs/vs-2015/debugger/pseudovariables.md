---
title: Sözde değişkenler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693762"
---
# <a name="pseudovariables"></a>Sözde Değişkenler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sözde değişkenler, belirli bilgileri bir değişken penceresinde veya **QuickWatch** iletişim kutusunda göstermek için kullanılan terimlerdir. Bir sözde değişkeni, normal bir değişkene girebileceğiniz şekilde girebilirsiniz. Ancak sözde değişkenler, değişken değildir ve programınızdaki değişken adlarına karşılık gelmez.  
  
## <a name="example"></a>Örnek  
 Bir yerel kod uygulaması yazdığınızı ve uygulamanızda ayrılan tanıtıcı sayısını görmek istediğinizi varsayalım. **Gözcü** penceresinde, **ad** sütununa aşağıdaki sözde değişkeni girebilir ve sonra değerlendirmek için Return tuşuna basabilirsiniz:  
  
```  
$handles  
```  
  
 Yerel kodda, bu tabloda gösterilen sözde değişkenleri kullanabilirsiniz:  
  
|Sözde değişken|İşlev|  
|--------------------|--------------|  
|`$err`|SetLastError işleviyle birlikte ayarlanan son hata değerini görüntüler. Görüntülenen değer, GetLastError işlevinin ne döndürüleceğini gösterir.<br /><br /> `$err,hr`Bu değerin kodu çözülmüş biçimini görmek için kullanın. Örneğin, son hata 3 ise, şu şekilde `$err,hr` görüntülenir `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Uygulamanızda ayrılan tanıtıcı sayısını görüntüler.|  
|`$vframe`|Geçerli yığın çerçevesinin adresini görüntüler.|  
|`$tid`|Geçerli iş parçacığının iş parçacığı KIMLIĞINI görüntüler.|  
|`$env`|Dize görüntüleyicisinde ortam bloğunu görüntüler.|  
|`$cmdline`|Programı başlatan komut satırı dizesini görüntüler.|  
|`$pid`|İşlem kimliğini görüntüler.|  
|`$`*RegisterName*<br /><br /> veya<br /><br /> `@`*RegisterName*|Kayıt *RegisterName*'in içeriğini görüntüler.<br /><br /> Normalde kayıt adını girerek kayıt içeriğini görüntüleyebilirsiniz. Bu söz dizimini kullanmanız gereken tek zaman, YAZMAÇ adının bir değişken adını aşırı yükleyidir. Kayıt adı, geçerli kapsamdaki bir değişken adıyla aynıysa, hata ayıklayıcı adı değişken adı olarak yorumlar. Bu, `$` *RegisterName* veya `@` *RegisterName* yararlı olarak sunulur.|  
|`$clk`|Saat döngülerinde saati görüntüler.|  
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|  
|`$exceptionstack`|Geçerli Windows Çalışma Zamanı özel durumunun yığın izlemesini görüntüler. `$ exceptionstack` yalnızca Windows 8.1 veya üzeri sürümlerde çalışan Mağaza uygulamalarında çalışır. `$ exceptionstack` C++ ve özel durumlar için desteklenmez|  
|`$ReturnValue`|Bir .NET Framework yönteminin dönüş değerini görüntüler. Bkz. [metot çağrılarının dönüş değerlerini inceleme](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 C# ve Visual Basic içinde, bu tabloda gösterilen sözde değişkenleri kullanabilirsiniz:  
  
|Sözde değişken|İşlev|  
|--------------------|--------------|  
|`$exception`|Son özel durum hakkındaki bilgileri görüntüler. Bir özel durum oluştuysa, değerlendirmek `$exception` bir hata mesajı görüntüler.<br /><br /> Yalnızca Visual C# ' de, özel durum Yardımcısı devre dışı bırakıldığında, `$exception` özel durum oluştuğunda otomatik olarak **Yereller** penceresine eklenir.|  
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgilerine sahip bir yapı görüntüler. Güvenlik nedenleriyle parola bilgileri gösterilmez.|  
  
 Visual Basic, aşağıdaki tabloda gösterilen sözde değişkenleri kullanabilirsiniz:  
  
|Sözde değişken|İşlev|  
|--------------------|--------------|  
|`$delete` veya `$$delete`|**Komut** penceresinde oluşturulan örtük bir değişkeni siler. Söz dizimi `$delete,` *değişken* veya `$delete,` *değişkendir*`.`|  
|`$objectids` veya `$listobjectids`|Tüm etkin nesne kimliklerini belirtilen ifadenin alt öğesi olarak görüntüler. Söz dizimi `$objectid,` *ifade* veya `$listobjectids,` *ifadedir*`.`|  
|`$` *N* `#`|Nesne KIMLIĞIYLE birlikte *N*değerine eşit olan nesneyi görüntüler.|  
|`$dynamic`|Uygulayan bir nesne için özel **Dinamik görünüm** düğümünü görüntüler `IDynamicMetaObjectProvider` . Arayüz. Sözdizimi `$dynamic,` *Object*. Bu özellik yalnızca .NET Framework sürüm 4 kullanan kod için geçerlidir. Bkz. [Dinamik görünüm](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve hızlı gözcü pencereleri](../debugger/watch-and-quickwatch-windows.md)   
 [Değişken pencereleri](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)

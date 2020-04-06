---
title: SccGetParentProjectPath Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700713"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath fonksiyonu
Bu işlev, belirtilen bir projenin ana proje yolunu belirler. Bu işlev, kullanıcı kaynak denetimine bir Visual Studio projesi eklendiğinde çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parametreler
 Pcontext

[içinde] Kaynak denetimi eklentibağlam işaretçisi.

 Hwnd

[içinde] Kaynak denetim eklentisinin sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresine bir tanıtıcı.

 lpUser

[içinde, dışarı] Kullanıcı adı (NULL sonlandırıcı dahil olmak üzere SCC_USER_SIZE'a kadar).

 lpProjPath

[içinde] Proje yolunu tanımlayan dize (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpAuxProjPath

[içinde, dışarı] Projeyi tanımlayan yardımcı dize (NULL sonlandırıcı dahil SCC_PRJPATH_SIZE kadar).

 lpParentProjPath

[içinde, dışarı] Ana proje yolunu tanımlayan çıktı dizesi (NULL sonlandırıcıdahil SCC_PRJPATH_SIZE kadar).

## <a name="return-value"></a>Döndürülen değer
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Üst proje yolu başarıyla elde edildi.|
|SCC_E_INITIALIZEFAILED|Proje başharfe alınamadı.|
|SCC_E_INVALIDUSER|Kullanıcı kaynak denetim eklentisinde oturum açamadı.|
|SCC_E_UNKNOWNPROJECT|Proje kaynak denetim eklentisi için bilinmemektedir.|
|SCC_E_INVALIDFILEPATH|Geçersiz veya kullanılamaz dosya yolu.|
|SCC_E_NOTAUTHORIZED|Kullanıcının bu işlemi gerçekleştirmesine izin verilmez.|
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemine erişmede büyük olasılıkla ağ veya çekişme sorunları nedeniyle bir sorun vardı. Yeniden deneme önerilir.|
|SCC_E_PROJSYNTAXERR|Geçersiz proje sözdizimi.|
|SCC_E_CONNECTIONFAILURE|Mağaza bağlantısı sorunu.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nonspesifik bir hata.|

## <a name="remarks"></a>Açıklamalar
 Bu işlev bir başarı veya hata kodu döndürür `lpParentProjPath` ve başarılı olursa, değişkeni belirtilen projeye tam proje yolu ile doldurur.

 Bu işlev, varolan bir projenin ana proje yolunu döndürür. Kök proje için işlev, geçirilen proje yolunu (yani aynı kök proje yolu) döndürür. Proje yolunun yalnızca kaynak denetim eklentisi için anlamlı bir dize olduğunu unutmayın.

 IDE, `lpUser` parametrelerde ve `lpAuxProjPath` parametrelerde yapılan değişiklikleri de kabul etmeye hazırdır. IDE bu dizeleri devam edecek ve kullanıcı gelecekte bu projeyi açtığında [SccOpenProject](../extensibility/sccopenproject-function.md) bunları geçmek. Bu dizeleri, bu nedenle, kaynak denetim eklentisi için bir proje ile ilişkilendirmek için gereken bilgileri izlemek için bir yol sağlar.

 Bu işlev [SccGetProjPath](../extensibility/sccgetprojpath-function.md)benzer , bir proje seçmek için kullanıcı istemi değil dışında. Ayrıca hiçbir zaman yeni bir proje oluşturmaz, ancak yalnızca varolan bir projeyle çalışır.

 Çağrıldığında `SccGetParentProjectPath` `lpProjPath` ve `lpAuxProjPath` boş olmayacak ve geçerli bir projeye karşılık gelecektir. Bu dizeleri genellikle `SccGetProjPath` işleviçin önceki bir çağrıdan IDE tarafından alınır.

 `lpUser` Bağımsız değişken kullanıcı adıdır. IDE, `SccGetProjPath` daha önce işlevden aldığı kullanıcı adından geçer ve kaynak denetim eklentisi varsayılan olarak adı kullanmalıdır. Kullanıcının eklentiyle zaten açık bir bağlantısı varsa, eklenti işlevin sessizce çalıştığından emin olmak için herhangi bir istemleri ortadan kaldırmaya çalışmalıdır. Ancak, oturum açma başarısız olursa, eklenti kullanıcıdan oturum açma için istekte olmalı ve geçerli bir giriş `lpUser`aldığında adı 'ne geri geçirin. Eklenti bu dizeyi değiştirebileceğinden, IDE her zaman bir boyut`SCC_USER_LEN`arabelleği (+1) ayırır. Dize değiştirilirse, yeni dize geçerli bir giriş adı olmalıdır (en azından eski dize kadar geçerlidir).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath için teknik notlar
 Kaynak denetimine çözüm ve proje ekleme, bir kullanıcıdan kaynak denetim sistemindeki konumları seçme sini en aza indirmek için Visual Studio'da basitleştirilmiştir. Bir kaynak kontrol eklentisi hem yeni işlevleri, [SccCreateSubProject'i](../extensibility/scccreatesubproject-function.md) hem de `SccGetParentProjectPath` işlevi destekliyorsa, bu değişiklikler Visual Studio tarafından etkinleştirilir. Ancak, aşağıdaki kayıt defteri girişi bu değişiklikleri devre dışı bırakıp önceki Visual Studio'ya (Kaynak Denetimi Eklentisi Eklentisi API Sürüm 1.1) davranışına geri dönmek için kullanılabilir:

 **[HKEY_CURRENT_USER\Yazılım\Microsoft\VisualStudio\8.0\Kaynak Denetimi] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Bu kayıt defteri girişi yoksa veya dword:00000000 olarak ayarlanmışsa, Visual `SccCreateSubProject`Studio`SccGetParentProjectPath`yeni işlevleri kullanmaya çalışır ve .

 Kayıt defteri girişi dword:00000001 olarak ayarlanmışsa, Visual Studio bu yeni işlevleri ve Visual Studio'nun önceki sürümlerinde olduğu gibi kaynak denetimi çalışmasına ekleme işlemlerini kullanmaya çalışmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi API fonksiyonları](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

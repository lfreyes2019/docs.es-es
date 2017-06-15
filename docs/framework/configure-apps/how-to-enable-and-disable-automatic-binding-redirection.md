---
title: "C&#243;mo: Habilitar y deshabilitar redireccionamiento de enlaces autom&#225;tico | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ensamblados [.NET Framework], redirección de enlaces"
  - "ejecución en paralelo, redirección de enlaces de ensamblados"
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# C&#243;mo: Habilitar y deshabilitar redireccionamiento de enlaces autom&#225;tico
A partir de [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], al compilar aplicaciones destinadas a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], las redirecciones de enlace se pueden agregar automáticamente al archivo de configuración de la aplicación para anular la unificación de ensamblados.  Las redirecciones de enlace se agregan si la aplicación o sus componentes hacen referencia a más de una versión del mismo ensamblado, incluso si se especifican manualmente las redirecciones de enlace en el archivo de configuración de la aplicación.  La característica de redirección de enlace automática afecta a las aplicaciones web y de escritorio tradicionales destinadas a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], aunque su comportamiento es ligeramente diferente para una aplicación web.  Puede habilitar la redirección de enlace automática si tiene aplicaciones existentes cuyo destino son versiones anteriores de .NET Framework o puede deshabilitar esta característica si desea conservar las redirecciones de enlace creadas manualmente.  
  
## Deshabilitar las redirecciones de enlace automáticas en aplicaciones de escritorio  
 Las redirecciones de enlace automáticas están habilitadas de forma predeterminada para las aplicaciones de escritorio tradicionales destinadas a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] y versiones posteriores.  Las redirecciones de enlace se agregan al archivo de configuración de salida \(app.config\) cuando la aplicación se compila y se invalida la unificación de ensamblados que puede producirse en caso contrario.  El archivo app.config de origen no se modifica.  Puede deshabilitar esta característica si modifica el archivo de proyecto para la aplicación.  
  
#### Para deshabilitar las redirecciones de enlace automáticas  
  
1.  En Visual Studio, seleccione el proyecto en el **Explorador de soluciones** y elija **Abrir carpeta en el Explorador de archivos** en el menú contextual.  
  
2.  En el Explorador de archivos, busque el archivo de proyecto \(.csproj o .vbproj\) y ábralo en Bloc de notas.  
  
3.  En el archivo de proyecto, busque la siguiente entrada de propiedad:  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  Cambie `true` a `false`:  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## Habilitar redirecciones de enlace automáticas manualmente  
 Puede habilitar las redirecciones de enlace automáticas en las aplicaciones existentes destinadas a versiones anteriores de .NET Framework, o en casos en que no se le pide automáticamente que agregue una redirección.  Si su objetivo es una versión más reciente del marco de trabajo, pero no se le pide automáticamente que agregue una redirección, probablemente obtendrá una salida de la compilación que le sugiere reasignar los ensamblados.  
  
#### Para agregar manualmente una propiedad de redirección de enlace automática  
  
1.  En Visual Studio, seleccione el proyecto en el **Explorador de soluciones** y elija **Abrir carpeta en el Explorador de archivos** en el menú contextual.  
  
2.  En el Explorador de archivos, busque el archivo de proyecto \(.csproj o .vbproj\) y ábralo en Bloc de notas.  
  
3.  Agregue el elemento siguiente al primer grupo de propiedades de configuración \(bajo la etiqueta \<PropertyGroup\>\):  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     En el ejemplo siguiente se muestra un archivo de proyecto con el elemento insertado.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProjectGuid>{123334}</ProjectGuid>  
        ...  
        <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>  
      </PropertyGroup>  
    ...  
    </Project>  
  
    ```  
  
4.  Compile la aplicación.  
  
## Habilitar las redirecciones de enlace automáticas en aplicaciones web  
 Las redirecciones de enlace automáticas se implementan de forma diferente para las aplicaciones web.  Puesto que el archivo de configuración de origen \(web.config\) debe modificarse para las aplicaciones web, las redirecciones de enlace no se agregan de forma automática al archivo de configuración.  Sin embargo, Visual Studio le notifica los conflictos de enlace, por lo que podrá agregar redirecciones de enlace para resolverlos.  Puesto que siempre se le preguntará si desea agregar redirecciones de enlace, no necesita deshabilitar explícitamente esta característica para una aplicación web.  
  
#### Para agregar redirecciones de enlace a un archivo web.config  
  
1.  En Visual Studio, compile la aplicación y compruebe si hay advertencias de compilación.  
  
     ![Advertencia de compilación para conflictos de referencia de ensamblado](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR\_AssemblyRefWarning")  
  
2.  Si hay conflictos de enlace de ensamblados, se mostrará una advertencia.  Haga doble clic en la advertencia.  \(Teclado: seleccione la advertencia y presione **Entrar**\).  
  
     Aparecerá un cuadro de diálogo que permite agregar automáticamente las redirecciones de enlace necesarias para el archivo web.config de origen.  
  
     ![Cuadro de diálogo de permiso de redireccionamiento de enlace](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR\_AddBindingRedirect")  
  
## Vea también  
 [Elemento \<bindingRedirect\>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)   
 [Redirigir versiones de ensamblado](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
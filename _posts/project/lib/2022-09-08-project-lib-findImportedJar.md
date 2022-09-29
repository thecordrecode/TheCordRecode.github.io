---
title: 자바로 Imported 된 자바 클래스 찾기
author: kimjeahyun
date: 2022-09-08 12:00:00 +0900
categories: [Projects,Lib]
tags: [Projects,Lib]
---

# 자바로 imported된 자바 클래스 찾기

사용법

packageNames에 내가 찾고자하는 패키지 삽입
extention에 확장자명 기입
directory에 최상위 폴더 지정

```java

package searchlib;

import java.io.File;
import java.io.FileNotFoundException;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

import com.google.common.io.Files;

public class FindFile  {
	public static List<String> FileList = new ArrayList<String>();
	
	public boolean isincludeString(String text,String name) {
		boolean isok = false;
		if(name.equals("")) return isok;
		if(text.split(name).length > 1) {
			isok = true;
		}
		return isok;
	}
	
	public boolean checkImported(String PackageName,String path) throws FileNotFoundException {
		File myObj = new File(path);
		Scanner myReader = new Scanner(myObj);
		boolean isok = false;
		
		while(myReader.hasNextLine())
		{
			String data = myReader.nextLine();
			
			int length  = data.split(" ").length;
			if(length == 2) {
				String isImported = data.split(" ")[0];
				String packageName = data.split(" ")[1];
				if(isImported.equals("import")) {
					if(isincludeString(packageName,PackageName)) {
						isok = true;
					}
					
				}
				
			}
			
		}
		myReader.close();
		return isok;
	}
	
	public void findFile(String PackageName,String name,File file) {
		File[] list = file.listFiles();
		if(list!=null)
			for(File fil:list)
			{
				if(fil.isDirectory())
				{
					findFile(PackageName,name,fil);
				}
				else {
					//System.out.println(fil.getAbsolutePath());
					String extension = Files.getFileExtension(fil.getName());
					if(extension.equals(name)) {
						try {
							boolean isok = checkImported(PackageName,fil.getAbsolutePath());
							if(isok == true) {
								FileList.add("###################  "+PackageName+"  ###################");
								FileList.add(fil.getAbsolutePath());
							}
							
						} catch (FileNotFoundException e) {
							// TODO Auto-generated catch block
							e.printStackTrace();
						}
					}
				}
			}
	}
	

	public static void main(String[] args) throws FileNotFoundException {
		
		FindFile ff = new FindFile();
		String extention = "java";
		String[] packageNames = {"javax","util","utils"};
		
		String directory = "C:\\Users\\kangt\\eclipse-workspace\\editds2";
		for(String paN:packageNames) {
			ff.findFile(paN,extention,new File(directory));
		}
		
		
		for(String item : FileList) {
			System.out.println(item);
		}
		
		
	}
	
}

```
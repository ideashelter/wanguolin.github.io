---
layout: post
title: "��δ�Git����ɾ��һ���ļ�"
description: ""
category: ����
tags: [Git]
---
{% include JB/setup %}

����������[Remove sensitive data][1]��ƪ���£��Һܿ�����������������Ƚ�ɵ�����������Ҳ���¸�д�Ĳ��Ͳ����ˡ�

Git��Ƶĳ��Ծ���ȷ��ÿһ�������Ǳ���¼�ڰ��ģ�����git��ֱ�Ӳ���ֻ����һ���ļ�����track��remove���������ڴ�֮ǰ������ļ������ֲ���������Ȼ�Ǽ�¼�ڰ���������Զ���ڵġ���������Ҫ�ȴӱ��ص���ʷ��¼�г������й�������ļ��ļ�¼��

    git filter-branch --force --index-filter \
        'git rm --cached --ignore-unmatch your_file' \
        --prune-empty --tag-name-filter cat -- --all

git filter-branch --index-filter ���Խ���һ�������Ϊ��branch�Ĳ�����your_file��Ҫ������ļ�����--prune-empty --tag-name-filter cat ���Կ��ύ�����������֮ǰ�ύ��ע����Ϣ�ȡ�����ʾ��
    
    Rewrite xxxxxx (xx/xx)
    Ref 'refs/heads/master' was rewritten

�Ӵ���ɾ�����ļ������߼���.gitignore���ύ��repo��

    git push origin master --force


��������һ����������ķ���̫�����ˣ���ô��ǿ�ҽ����㳢�����¹���[BFG][2]��

��������й��ߵ�[�÷�][3]����������ɾ��ָ���ļ����������Զ�ɾ�����ڶ���M�ļ����ȵȡ�ԭ���filter-branch���ơ���������ɾ��ָ���ļ�Ϊ����

     git clone --mirror git://github.com/repo.git
     java -jar bfg.jar --delete-files filename repo.git
     git push







[1]:http://help.github.com/articles/remove-sensitive-data
[2]:http://repo1.maven.org/maven2/com/madgag/bfg/1.11.0/bfg-1.11.0.jar (bfg-repo-cleaner)
[3]:http://rtyley.github.io/bfg-repo-cleaner/

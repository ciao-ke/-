void del(p** arr, p** back)
{
	printf("请选择您的查找方式：\n1.职工号\n2.姓名\n3.基本工资低于1000人员\n");
	nouse = scanf("%d", &way);
	search(way, arr, back);
	if (back[0] != NULL)
	{
		int target = 1;
		if (back[1] != NULL)
		{
			show(back);
			printf("请选择您要删除的序号：");
			nouse = scanf("%d", &target);
		}
		memset(back[target - 1], 0, sizeof(struct person));
		if (back[target - 1] != 0)
		{
			for (int i = 0; i < 1000; i++)
			{
				if (!strcmp(arr[i]->id, back[target - 1]->id))
				{
					//free(arr[i]);
					for (int x = i + 1; x < 1000; x++)
					{
						arr[x - 1] = arr[x];
					}
					arr[999] = NULL;
					break;
				}
			}
			printf("删除成功！\n");
		}
		else
			printf("删除失败！\n");
	}
}

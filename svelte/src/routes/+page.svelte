<script>
    import { ProgressBar } from '@skeletonlabs/skeleton';
    import { Accordion, AccordionItem } from '@skeletonlabs/skeleton';

    export let title = "임금체불날짜트래커";

    const summary1 = "무슨 일이 일어난거죠?";
    const summary2 = "언제 해결될 수 있나요?";
    const summary3 = "어떻게 해야 하죠?";
    
    const answer1 = "월급이 안나와요! 너무 급작스럽게 닥친 일이라 천 명 넘는 사람들의 삶이 불안정해졌어요.";
    const answer2 = "월급은 언제 들어올까요? 누가 의사결정 권한을 갖고 있었고, 누가 책임지는 건가요? 누구도 알 수 없어요! 원래 세상이 그런건가봐요!";
    const answer3 = "하지만 Don't Panic. 각자 상황에 맞춰 기준을 정하고 최선의 판단을 해보세요. 너무 비관적인 생각도, 너무 낙관적인 생각도 금물.";

    const date = Math.floor((new Date() - new Date(2024, 8, 23)) / (1000 * 60 * 60 * 24));

    const today = new Date();
    const currentDay = today.getDate();
    const currentMonth = today.getMonth();

    const lastPayday = new Date(today);
    lastPayday.setDate(25);
    if (currentDay < 25) {
        lastPayday.setMonth(currentMonth - 1);
    }

    const nextPayday = new Date(today);
    nextPayday.setDate(25);
    if (currentDay >= 25) {
        nextPayday.setMonth(currentMonth + 1);
    }

    const daysSinceLastPayday = Math.floor((today - lastPayday) / (1000 * 60 * 60 * 24));
    const daysUntilNextPayday = Math.floor((nextPayday - today) / (1000 * 60 * 60 * 24));
</script>

<svelte:head>
  <title>{title}</title>
</svelte:head>

<div class="flex justify-center items-center min-h-screen">
    <div class="p-8 w-full sm:w-full md:w-10/12 lg:w-8/12 xl:w-6/12 max-w-2xl">
        <div class="mt-8 text-center text-4xl font-pretendard py-4">
            임금체불 공지일로부터
        </div>
        <div class="text-center text-8xl py-2">
            {date}일 
        </div>

        <div>
            {#if daysSinceLastPayday === 0}
            <div class="text-center text-xl font-pretendard mt-4">
                오늘은 슈퍼앱같은 월급날! 🎉💰🎊🤮
            </div>
            {:else}
            <div class="text-center text-xl font-pretendard mt-4">
                지난 월급날로부터 {daysSinceLastPayday}일 지났습니다
            </div>
            {/if}
            <div class="text-center text-xl font-pretendard mt-2">
            다음 월급날까지 {daysUntilNextPayday}일 남았습니다
            </div>
        </div>

        <div class="text-center font-pretendard mt-4">
            급여 로딩 중... (20/100 %)
        </div>
        <div class="w-full sm:w-3/4 md:w-1/2 lg:w-1/3 xl:w-1/4 mx-auto py-2">
            <ProgressBar value={undefined} />
        </div>

        <div class="py-8">
            <Accordion>
                <AccordionItem open>
                    <svelte:fragment slot="lead"><i class="fa-solid fa-question"></i></svelte:fragment>
                    <svelte:fragment slot="summary">{summary1}</svelte:fragment>
                    <svelte:fragment slot="content">{answer1}</svelte:fragment>
                </AccordionItem>
                <AccordionItem>
                    <svelte:fragment slot="lead"><i class="fa-regular fa-clock"></i></svelte:fragment>
                    <svelte:fragment slot="summary">{summary2}</svelte:fragment>
                    <svelte:fragment slot="content">{answer2}</svelte:fragment>
                </AccordionItem>
                <AccordionItem>
                    <svelte:fragment slot="lead"><i class="fa-regular fa-comment"></i></svelte:fragment>
                    <svelte:fragment slot="summary">{summary3}</svelte:fragment>
                    <svelte:fragment slot="content">{answer3}</svelte:fragment>
                </AccordionItem>
            </Accordion>
        </div>
    </div>
</div>

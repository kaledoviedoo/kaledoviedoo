

# Hi there! ✋

I'm **Kaled**, a Systems Engineering student and developer based in Colombia.

I love building web applications, designing user interfaces, and creating workflow automations that simplify processes.

Outside of code and design, you'll find me exploring new tech, working on creative projects, or sharing my work. Check out more of me on [Instagram](https://www.instagram.com/kaledoviedo/) or reach out via [Email](mailto:kaledoviedoo@gmail.com).

**Fun Facts:**
* Studying Systems Engineering at Escuela Colombiana de Ingeniería Julio Garavito.
* Currently learning about data analytics and bot automation and finances. 
* Passionate about making your workflow easier and building smooth digital experiences.

![Top Languages](https://ghstats.dev/api/langs?username=kaledoviedoo&theme=gruvbox)

**Recent Activity**

![Contribution Sparkline](https://ghstats.dev/api/sparkline?username=kaledoviedoo&theme=gruvbox&days=90&width=320&height=80)

"use client";

import {
  ContributionGraph,
  ContributionGraphBlock,
  ContributionGraphCalendar,
  ContributionGraphFooter,
  ContributionGraphLegend,
  ContributionGraphTotalCount,
} from "@/components/kibo-ui/contribution-graph";
import { eachDayOfInterval, endOfYear, formatISO, startOfYear } from "date-fns";

const maxCount = 20;
const maxLevel = 4;
const now = new Date();
const days = eachDayOfInterval({
  start: startOfYear(now),
  end: endOfYear(now),
});

const data = days.map((date) => {
  const c = Math.round(
    Math.random() * maxCount - Math.random() * (0.8 * maxCount)
  );
  const count = Math.max(0, c);
  const level = Math.ceil((count / maxCount) * maxLevel);

  return {
    date: formatISO(date, { representation: "date" }),
    count,
    level,
  };
});

const Example = () => (
  <ContributionGraph blockMargin={2} blockSize={20} data={data} fontSize={16}>
    <ContributionGraphCalendar>
      {({ activity, dayIndex, weekIndex }) => (
        <ContributionGraphBlock
          activity={activity}
          dayIndex={dayIndex}
          weekIndex={weekIndex}
        />
      )}
    </ContributionGraphCalendar>
    <ContributionGraphFooter>
      <ContributionGraphTotalCount />
      <ContributionGraphLegend />
    </ContributionGraphFooter>
  </ContributionGraph>
);

export default Example;


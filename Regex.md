using System.Text.RegularExpressions;

string str = "abc1234def56";
    Regex rx = new Regex("def");

    //메타문자 사용
    MatchCollection matches = Regex.Matches(str, @"\d+");
    foreach (Match match in matches)
    {
        Console.WriteLine(match.Value);
    }
    
    Match a = Regex.Match(str, "34de");
    Console.WriteLine(a);

    //카운트 속성 사용 예시
    Console.WriteLine("{0} matches found in:\n   {1}", matches.Count, str);


    // 메서드 사용 예시
    foreach (Match match in matches)
    {
        GroupCollection groups = match.Groups;
        Console.WriteLine("'{0}' repeated at positions {1} and {2}",
                          groups["word"].Value,
                          groups[0].Index,
                          groups[1].Index);
    }

    //Success: 일치하는 문자열을 찾았는지 여부를 가져옵니다.
    //Value: 일치하는 문자열을 가져옵니다.
    //Index: 일치하는 문자열의 시작 위치를 가져옵니다.
    //Length: 일치하는 문자열의 길이를 가져옵니다.
    //Groups: 일치하는 문자열의 하위 그룹을 가져옵니다.


    //메타문자 사용 예시
    MatchCollection mc = Regex.Matches(str, @"^강\w*구$");

    //    메타문자 의미
    //------------------------
    //^라인의 처음
    //$        라인의 마지막    
    //\w 문자(영숫자) [a-zA - Z_0 - 9]
    //\s Whitespace(공백, 뉴라인, 탭..)
    //\d 숫자
    //*Zero 혹은 그 이상
    //+ 하나 이상
    //? Zero 혹은 하나
    //.        Newline을 제외한 한 문자
    //[]      가능한 문자들
    //[^ ]     가능하지 않은 문자들
    //[- ]    가능 문자 범위
    //{ n,m}
    //    최소 n개, 최대 m개
    //()     그룹
    //| 논리 OR
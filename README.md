//점수를 입력받아서 석차를 만드는 코드
package JAVA002;
import java.util.Scanner;

public class kdooone1{
	public static void main(String[] args) {
		
		Scanner scanner = new Scanner(System.in);
		String qwe = "yes";
		boolean zxc;
		
		do{
		//다차원 배열의 행을 정할 학생수를 입력받는다
		
			System.out.print("학생 수를 입력해주세요. ");
			int abcd;
			try {
			    abcd = Integer.parseInt(scanner.nextLine()); // 개행 문자 소비
			} catch (NumberFormatException e) {
			    System.out.println("숫자로만 입력 바랍니다.");
			    System.out.println("다시 진행합니다.");
			    continue; // 잘못된 입력을 받으면 반복문의 처음으로 돌아감
			}
   
      	 //입력받은 학생수로 행을 정의 한다 
        //열의 크기 정의
 	String[][] studentData = new String[abcd][8]; 
        
 		int cccc = 1;
        //여기서 정보들을 입력받아 저장한다
        for (int i = 0; i < abcd; i++) {
            System.out.print("학생 이름을 입력해주세요 ");
            studentData[i][0] = String.valueOf(cccc);
            studentData[i][1] = scanner.next();
            cccc++;
            System.out.println(studentData[i][0] + " 학생의 성적을 순서대로 입력해주세요 (국어 영어 수학 순으로)");
            for (int j = 2; j <= 4; j++) {
                System.out.print("과목 성적을 입력하세요 ");
                studentData[i][j] = scanner.next();
            }
        }
        
        //Double.parseDouble(변수이름)  문자열을 실수로 변환하는 메서드
        for (int i = 0; i < abcd; i++) {
            // 총점 계산
           int total = Integer.parseInt(studentData[i][2]) + 
            			   Integer.parseInt(studentData[i][3]) + 
            			   Integer.parseInt(studentData[i][4]);
            
            studentData[i][5] = String.valueOf(total);
            
            // 평균 계산
            double average = Math.floor((total / 3.0) * 10) / 10; // 평균을 소수점 한 자리까지 계산
            studentData[i][6] = Double.toString(average);
        }
        
     // 석차 계산
        for (int i = 0; i < abcd; i++) {
            int ra = 1; // 초기 석차는 1로 설정
            for (int j = 0; j < abcd; j++) {
                if (Double.parseDouble(studentData[i][5]) < Double.parseDouble(studentData[j][5])) {    
                    ra++;
                }
            }
            studentData[i][7] = String.valueOf(ra); 
        }
        
       //결과를 출력한다
        System.out.println("---------------------------------------------------------------------------");
        System.out.println("				성적표				");
        System.out.println("---------------------------------------------------------------------------");
        System.out.println("번호\t이름\t국어\t영어\t수학\t총점\t평균\t석차");
        System.out.println("---------------------------------------------------------------------------");
        
        for (int i = 0; i < abcd; i++) {
            System.out.print(studentData[i][0] + "\t");
            System.out.print(studentData[i][1] + "\t");
            for (int j = 2; j <= 4; j++) {
                System.out.print(studentData[i][j] + "\t");
            }
            System.out.println(studentData[i][5] + "\t" + studentData[i][6]+ "\t" + studentData[i][7]);
        }
        
        System.out.println("---------------------------------------------------------------------------");
    
		//프로그램을 다시 진행할지 물어보고 종료할지 다시 진행할지 정한다
		 System.out.println("게속 진행할까요?");
		 System.out.println("yes 또는 no 로 입력바랍니다.");
		 scanner.nextLine(); 
		 qwe = scanner.nextLine();
		 
		
	} while(qwe.equals("yes"));
	    }
	}


import SwiftUI

struct LabReportEntryScreen: View {
    @State private var hemoglobin: String = ""
    @State private var hematocrit: String = ""
    @State private var platelets: String = ""
    @State private var wbc: String = ""
    @State private var inr: String = ""

    var body: some View {
        NavigationView {
            ZStack {
                // Dark background
                Color(.black)
                    .edgesIgnoringSafeArea(.all)

                ScrollView {
                    VStack(spacing: 18) {

                        // Patient Card
                        VStack(alignment: .leading, spacing: 10) {
                            HStack(spacing: 14) {
                                Circle()
                                    .fill(Color(.systemMint).opacity(0.45))
                                    .frame(width: 42, height: 42)
                                    .overlay(
                                        Image(systemName: "person.fill")
                                            .foregroundColor(.teal)
                                            .font(.system(size: 22))
                                    )
                                VStack(alignment: .leading, spacing: 4) {
                                    Text("Michael Chen")
                                        .foregroundColor(.white)
                                        .font(.system(size: 16, weight: .semibold))
                                    Text("ID: P002 • 67y, Male")
                                        .foregroundColor(.gray)
                                        .font(.system(size: 13))
                                }
                            }
                            VStack(alignment: .leading, spacing: 3) {
                                HStack(spacing: 0) {
                                    Text("Tests Ordered: ")
                                        .font(.system(size: 13, weight: .medium))
                                        .foregroundColor(.gray)
                                    Text("CBC, Lipid Panel, Basic Metabolic Panel")
                                        .font(.system(size: 13))
                                        .foregroundColor(.white)
                                }
                                Text("Ordering Physician: Dr. Smith")
                                    .font(.system(size: 13))
                                    .foregroundColor(.gray)
                            }
                            .padding(.top, 6)
                        }
                        .padding(16)
                        .background(Color(.darkGray))
                        .cornerRadius(12)
                        .shadow(color: Color(.black).opacity(0.7), radius: 1, x: 0, y: 0)
                        .padding([.horizontal, .top], 10)

                        // Hematology Section
                        VStack(alignment: .leading, spacing: 16) {
                            HStack(spacing: 6) {
                                Image(systemName: "testtube.2")
                                    .foregroundColor(.teal)
                                Text("Hematology")
                                    .font(.system(size: 16, weight: .bold))
                                    .foregroundColor(.white)
                            }
                            VStack(alignment: .leading, spacing: 12) {
                                LabeledEntryField(label: "Hemoglobin", normal: "12–16 g/dL", placeholder: "Enter value (g/dL)", text: $hemoglobin, isDark: true)
                                LabeledEntryField(label: "Hematocrit", normal: "36–46 %", placeholder: "Enter value (%)", text: $hematocrit, isDark: true)
                                LabeledEntryField(label: "Platelets", normal: "150–450 x 10^9/uL", placeholder: "Enter value (x 10^9/uL)", text: $platelets, isDark: true)
                                LabeledEntryField(label: "White Blood Cells", normal: "4.5–11 x 10^9/uL", placeholder: "Enter value (x 10^9/uL)", text: $wbc, isDark: true)
                            }
                        }
                        .padding(16)
                        .background(Color(.darkGray))
                        .cornerRadius(12)
                        .shadow(color: Color(.black).opacity(0.7), radius: 1, x: 0, y: 0)
                        .padding(.horizontal, 10)

                        // Coagulation Section
                        VStack(alignment: .leading, spacing: 16) {
                            HStack(spacing: 6) {
                                Image(systemName: "testtube.2")
                                    .foregroundColor(.teal)
                                Text("Coagulation")
                                    .font(.system(size: 16, weight: .bold))
                                    .foregroundColor(.white)
                            }
                            LabeledEntryField(label: "INR", normal: "0.8–1.1", placeholder: "Enter value", text: $inr, isDark: true)
                        }
                        .padding(16)
                        .background(Color(.darkGray))
                        .cornerRadius(12)
                        .shadow(color: Color(.black).opacity(0.7), radius: 1, x: 0, y: 0)
                        .padding(.horizontal, 10)

                        // Submit Button
                        Button(action: {
                            // Submit logic here
                        }) {
                            HStack {
                                Image(systemName: "doc.text.fill")
                                Text("Submit Lab Report")
                                    .fontWeight(.semibold)
                            }
                            .foregroundColor(.white)
                            .padding()
                            .frame(maxWidth: .infinity)
                            .background(Color.teal)
                            .cornerRadius(10)
                        }
                        .padding(.horizontal, 20)
                        .padding(.top, 8)
                        .padding(.bottom, 18)
                    }
                }
            }
            .navigationBarTitle("Lab Report Entry", displayMode: .inline)
            .toolbarBackground(Color(.black), for: .navigationBar)
            .toolbarBackground(.visible, for: .navigationBar)
            .toolbarColorScheme(.dark, for: .navigationBar)
        }
        .navigationViewStyle(StackNavigationViewStyle())
    }
}

// Custom field for label and normal value styling
struct LabeledEntryField: View {
    var label: String
    var normal: String
    var placeholder: String
    @Binding var text: String
    var isDark: Bool = false

    var body: some View {
        VStack(alignment: .leading, spacing: 5) {
            HStack {
                Text(label)
                    .font(.system(size: 14, weight: .semibold))
                    .foregroundColor(isDark ? .white : .black)
                Spacer()
                Text("(Normal: \(normal))")
                    .font(.system(size: 12))
                    .foregroundColor(.gray)
            }
            TextField(placeholder, text: $text)
                .padding(10)
                .background(isDark ? Color(.black).opacity(0.6) : Color(.systemGray6))
                .cornerRadius(8)
                .font(.system(size: 14))
                .foregroundColor(isDark ? .white : .black)
        }
    }
}

struct LabReportEntryScreen_Previews: PreviewProvider {
    static var previews: some View {
        LabReportEntryScreen()
            .preferredColorScheme(.dark)
    }
}


import matplotlib.pyplot as plt
from matplotlib.backends.backend_pdf import PdfPages
import numpy as np
from fpdf import FPDF
import io

# 创建PDF类
class PDF(FPDF):
    def header(self):
        if self.page == 1:
            # 首页头部
            self.set_font('Arial', 'B', 20)
            self.set_text_color(31, 73, 125)
            self.cell(0, 20, '量化金融学习完整指南', 0, 1, 'C')
            self.set_font('Arial', 'I', 12)
            self.set_text_color(100, 100, 100)
            self.cell(0, 10, '随机微积分与金融衍生品精通之路', 0, 1, 'C')
            self.ln(10)
        else:
            # 其他页头部
            self.set_font('Arial', 'I', 8)
            self.set_text_color(100, 100, 100)
            self.cell(0, 10, '量化金融学习指南', 0, 0, 'L')
            self.cell(0, 10, f'第 {self.page} 页', 0, 0, 'R')
            self.ln(10)

    def footer(self):
        self.set_y(-15)
        self.set_font('Arial', 'I', 8)
        self.set_text_color(100, 100, 100)
        self.cell(0, 10, '更多量化资源请访问: github.com/quant-resources', 0, 0, 'C')

    def chapter_title(self, title):
        self.set_font('Arial', 'B', 16)
        self.set_fill_color(240, 240, 240)
        self.set_text_color(31, 73, 125)
        self.cell(0, 10, title, 0, 1, 'L', 1)
        self.ln(5)

    def section_title(self, title):
        self.set_font('Arial', 'B', 12)
        self.set_text_color(59, 89, 152)
        self.cell(0, 8, title, 0, 1, 'L')
        self.ln(2)

    def content_text(self, text):
        self.set_font('Arial', '', 10)
        self.set_text_color(0, 0, 0)
        self.multi_cell(0, 6, text)
        self.ln(3)

    def bullet_point(self, text):
        self.set_font('Arial', '', 10)
        self.set_text_color(0, 0, 0)
        self.cell(5, 6, '•', 0, 0)
        self.multi_cell(0, 6, text)
        self.ln(2)

# 创建学习路线图
def create_learning_roadmap():
    fig, ax = plt.subplots(figsize=(10, 6))
    
    # 创建时间轴
    months = ['第1-2月', '第3-4月', '第5月', '第6月']
    topics = [
        '概率基础\n编程技能\n金融产品',
        '随机微积分\nBSM模型\n期权定价',
        '数值方法\n波动率模型\n利率模型', 
        '综合项目\n面试准备\n知识复盘'
    ]
    
    colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#96CEB4']
    
    # 创建甘特图
    for i, (month, topic, color) in enumerate(zip(months, topics, colors)):
        ax.barh(month, 2, left=i, height=0.6, color=color, alpha=0.8)
        ax.text(i + 1, i, topic, ha='center', va='center', fontsize=9, fontweight='bold')
    
    ax.set_xlabel('学习进度')
    ax.set_ylabel('时间阶段')
    ax.set_title('6个月量化金融学习路线图', fontsize=14, fontweight='bold')
    ax.set_xlim(0, 4)
    ax.grid(axis='x', alpha=0.3)
    
    plt.tight_layout()
    
    # 将图表转换为图像
    buf = io.BytesIO()
    plt.savefig(buf, format='png', dpi=150, bbox_inches='tight')
    buf.seek(0)
    plt.close()
    
    return buf

# 创建技能分布雷达图
def create_skills_radar():
    fig = plt.figure(figsize=(6, 6))
    ax = fig.add_subplot(111, polar=True)
    
    # 技能分类
    categories = ['数学基础', '编程能力', '金融知识', '随机分析', '数值方法', '实践项目']
    N = len(categories)
    
    # 技能值（0-100）
    values = [85, 90, 75, 80, 70, 85]
    
    # 计算角度
    angles = [n / float(N) * 2 * np.pi for n in range(N)]
    angles += angles[:1]
    values += values[:1]
    
    # 绘制雷达图
    ax.plot(angles, values, 'o-', linewidth=2, color='#45B7D1')
    ax.fill(angles, values, alpha=0.25, color='#45B7D1')
    
    # 设置标签
    ax.set_thetagrids([a * 180 / np.pi for a in angles[:-1]], categories)
    ax.set_ylim(0, 100)
    ax.set_title('量化分析师技能要求分布', size=14, color='#2E86AB', fontweight='bold')
    
    plt.tight_layout()
    
    buf = io.BytesIO()
    plt.savefig(buf, format='png', dpi=150, bbox_inches='tight')
    buf.seek(0)
    plt.close()
    
    return buf

# 生成PDF
def generate_quant_pdf():
    pdf = PDF()
    pdf.add_page()
    
    # 添加封面
    pdf.set_font('Arial', 'B', 24)
    pdf.set_text_color(31, 73, 125)
    pdf.cell(0, 50, '量化金融学习完整指南', 0, 1, 'C')
    
    pdf.set_font('Arial', 'I', 16)
    pdf.set_text_color(100, 100, 100)
    pdf.cell(0, 20, '随机微积分与金融衍生品精通之路', 0, 1, 'C')
    
    pdf.set_font('Arial', '', 12)
    pdf.set_text_color(0, 0, 0)
    pdf.cell(0, 10, '从业者推荐的系统学习路径与资源', 0, 1, 'C')
    
    pdf.ln(30)
    pdf.set_font('Arial', '', 10)
    pdf.cell(0, 10, '发布日期: 2024', 0, 1, 'C')
    
    # 添加目录
    pdf.add_page()
    pdf.chapter_title('目录')
    
    sections = [
        '1. 核心学习资源',
        '2. 6个月学习计划', 
        '3. 数学基础要求',
        '4. 编程实践指南',
        '5. 金融衍生品知识',
        '6. 随机微积分精要',
        '7. 实战项目建议',
        '8. 从业者建议'
    ]
    
    for section in sections:
        pdf.bullet_point(section)
    
    # 添加核心学习资源部分
    pdf.add_page()
    pdf.chapter_title('1. 核心学习资源')
    
    pdf.section_title('数学基础')
    resources = [
        'MIT 18.650 Statistics for Applications - 概率统计',
        'Harvard Stat 110 - 概率论基础课程',
        'YouTube: Mathified Measure Theory系列 - 测度论直观讲解',
        '《A First Course in Probability》by Sheldon Ross - 经典教材'
    ]
    
    for resource in resources:
        pdf.bullet_point(resource)
    
    pdf.section_title('随机微积分')
    stoch_resources = [
        'Steve Shreve公开课视频 - 直观理解布朗运动、伊藤积分',
        'MIT 18.S096 - 数学金融应用课程',
        'Luis Seco多伦多大学课程笔记 - 实战问题集',
        '《Stochastic Calculus for Finance II》by Steven Shreve - 行业圣经'
    ]
    
    for resource in stoch_resources:
        pdf.bullet_point(resource)
    
    # 添加学习计划部分
    pdf.add_page()
    pdf.chapter_title('2. 6个月高强度学习计划')
    
    roadmap_img = create_learning_roadmap()
    pdf.image(roadmap_img, x=10, y=None, w=180)
    pdf.ln(5)
    
    plan_details = [
        ('第1-2月: 基础搭建', '概率基础 + Python编程 + 金融产品知识'),
        ('第3-4月: 核心攻坚', '随机微积分 + BSM模型推导 + 期权定价实战'),
        ('第5月: 深化应用', '数值方法 + 波动率模型 + 利率衍生品'),
        ('第6月: 整合复盘', '综合项目 + 面试准备 + 知识体系梳理')
    ]
    
    for title, content in plan_details:
        pdf.section_title(title)
        pdf.content_text(content)
    
    # 添加技能要求图表
    pdf.add_page()
    pdf.chapter_title('3. 量化分析师技能要求')
    
    skills_img = create_skills_radar()
    pdf.image(skills_img, x=30, y=None, w=150)
    pdf.ln(5)
    
    # 添加实践建议
    pdf.add_page()
    pdf.chapter_title('8. 从业者终极建议')
    
    advice = [
        '理解"风险中性"概念 - 这是量化定价的第一性原理',
        '掌握希腊值计算与解释 - 不仅是风险指标，更是理解模型的窗口',
        '关注数据而非仅模型 - 真实赚钱能力来自对数据的理解和处理',
        '加入量化社区 - QuantNet、Wilmott Forums、r/quant',
        '保持耐心与重复学习 - 随机微积分需要三遍学习法'
    ]
    
    for i, item in enumerate(advice, 1):
        pdf.bullet_point(item)
    
    # 保存PDF
    pdf.output('quantitative_finance_learning_guide.pdf')
    return 'quantitative_finance_learning_guide.pdf'

# 生成PDF文件
pdf_path = generate_quant_pdf()
pdf_path
